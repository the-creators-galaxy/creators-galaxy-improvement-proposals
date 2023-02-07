- cgip: 4
- title: Community Governance & Voting Model
- author: @paulatcalaxy
- type: Standards Track 
- category: Core 
- status: Last Call
- created: January 15/2022
- discussions-to: 
- updated: Feb 7/2023
- requires: na
- replaces: na
- superseded-by: 

## Abstract

The Creator’s Galaxy is a community-governed social ecosystem. This specification describes a framework by which community members can propose features, economics and enhancements of the ecosystem, subsequently cast their votes on those propositions, and thereby directly influence its evolution. We believe that this framework and the corresponding open source software could be adopted by other communities in the Hedera ecosystem and leveraged for their own governance decisions and as such, contribute to the development of DAOs on Hedera.

## Motivation

The vision of the Creator’s Galaxy is that the community of Creators, Members, and applications will govern its evolution. This CGIP proposes a framework by which arbitrary participants of the community can propose new features or enhancements, and by which the broader community can vote either in favor or against that proposition - with their vote weighted by the number of $CLXY coins they own.

## Rationale

The governance architecture uses [Hedera Consensus Service](https://docs.hedera.com/guides/docs/sdks/consensus) (HCS) to provide an open, transparent and provable repository/database of propositions, votes, and ballot results. As the governance topic has no [submission keys](https://docs.hedera.com/guides/docs/sdks/consensus/create-a-topic); subject to optional constraints defined in a HCS topic (as described below), anyone can both submit a proposition and/or vote on one. As the HCS messages are archived on 3rd party mirror nodes, the history of propositions and votes is public and auditable.

The Creator’s Galaxy will be the first ecosystem to leverage this framework for its own governance but the model is designed such that it could be adopted by other decentralized communities on Hedera.

## User Stories

Proposers

1. A Proposer wants to create a new Proposition on which the community will vote
2. Proposer visits gov.creatorsgalaxy.com, an IPFS CID, or runs the the codebase locally, and indicates they wish to create a new proposition
3. Proposer provides necessary information to describe the proposition and details of the ballot
4. Proposer signs HCS transaction to submit the proposition 
5. Community is notified of the new proposition and its upcoming ballot details

Voters

1. A Voter becomes aware of a new proposition and decides they wish to vote on it
2. When the ballot opens, Voter visits gov.creatorsgalaxy.com, an IPFS CID, or runs the codebase locally, and finds the proposition
3. Voter researhes the previous discussions on the proposition
4. Voter signs an HCS message to cast their vote on the Proposition 

Scrutineers

1. A Scrutineer wants to determine the results of a ballot on a proposition once its ballot has closed
2. For the appropriate ballot, Scrutineer deterimines start and end times and scans the governance topic for votes cast within that period
3. Scrutineer validates each ballot and determines the signing account
4. Scrutineer retrieves the ballot's snapshot and weights each valid vote by the number of $CLXY within the signing account
5. Scrutineer adds up $CLXY weighted votes and determines result of ballot
6. Scrutineer computes a checksum of the data used to determine the results of the ballot that can be compared the checksums computed by of other scrutineers for comparison and validation.

## Specification

The following sections describe the proposition ballot framework

### High Level 

The voting process will allow community members to cast votes on governance ballots, these votes weighted by their $CLXY balances.

At high-level, the sequence of steps for a particular governance proposition is

1. The community will use the CGIP process to discuss an issue. 
2. After sufficient discussion, a member of the community will visit gov.creatorsgalaxy.com to create a proposition using a permitted (white-listed) Hedera Account. Note: the codebase being deployed at gov.creators.galaxy.com will also be available to be run locally. Further, each version should be distributed via IPFS, and accessible through it’s unique CID, to ensure it’s accessibility in the future. They will describe the feature or issue, link to previous CGIP discussions, and specify a start time for voting. 
3. Submitting the proposition will result in:
	* Community members will be informed of the proposition and details of the upcoming ballot via multiple channels (e.g. Discord, Twitter, in app, etc)
	* An HCS message will be submitted to an HCS Topic to record the above ballot terms with a `create-ballot` message. The HCS message’s consensus timestamp becomes the identifier for the proposal, and the account signing the transaction submitting the HCS message becomes the proposal’s author.
4. Members of the ecosystem, having subscribed to the above topic or receiving notification via other channels (e.g. Twitter, Discord, in app, etc), will be made aware of the upcoming ballot
5. For the purposes of weighted voting, the account holder’s $CLXY balance at the moment in time which the voting window opens is considered the weighted snapshot balance for that account holder.  Hedera Mirror nodes provide the balances of accounts at any time in history, and will be queried for this information when tabulating vote results. 
6. The HCS Voting stream configuration and/or ballot rules may identify accounts that may not be permitted to vote on any or all ballots.  The balances of these accounts will not be included when computing any required threshold quorum requriements.
7. For the duration of the proposal voting window, members of the community can submit votes as `cast-vote` messages against the above topic. These vote messages will indicate the Ballot identifier. These votes transactions will be signed by the private key(s) of the relevant Hedera account. If an account submits multiple `cast-vote` messages within the voting window for a given ballot, only the last will be counted.
8. Members of the community will collect and validate the voting messages during the period of the ballot.
9. The voting window will remain open for at least the minimum requirment specified in the HCS Voting stream rules, and may be lenghened beyond the required minimum by the proposal author. After the voting window closes, each vote will be weighted according to the $CLXY balance of the corresponding Hedera account at the time of the voting window opening.
10. The results of the ballot will be tallied and displayed by various software systems that can be both hosted and run independently by Scrutineers.


### Vote weighting

The votes of community members will be weighted by the amount of $CLXY they own within their Hedera account. Initially, the only weighting model supported will be '1 $CLXY = 1 vote'

An account's voting weight will be the $CLXY balance across all Hedera accounts at the time when the respective ballot opens for voting.

Both the HCS Voting Stream configuration and ballot definitions may list accounts that are not permitted to vote.  Their weighted $CLXY balance will not be taken into account when computing any required quorum threshold.

The HCS Voting Stream configuration and ballot may include a required voting threshold fraction, the necessary weighted amount of $CLXY that must participate in a vote to be considered a valid.  If this quorum is not satisfied, the vote is considered inconclusive.

$CLXY account holders voting *abstain* will be counted as having voted for quorum computation purposes.

The Hedera Mirror REST API provides a call to retrieve the balance of all accounts that hold $CLXY at a given point in time is similar to the following:

```
/api/v1/tokens/0.0.859814/balances?account.balance=gt:0&order=asc&timestamp=gte:[insert ballot id here]
```

### HCS Topics

All governance messages (ballot creation & votes) will be submitted against a single HCS governance topic.

There will be no restrictions on who can submit against this topic.  However, certain accounts may be designated as curators, and only proposals submitted by these accounts will be considered valid proposals.

The topic will be immutable.

The first message in the topic shall be a `define-rules` message outlining the Voting Stream configuration.  The information in this first message may include the white-list of accounts that may submit proposals, a global list of accounts that may not vote on any proposal, the minimum time required for voting windows, and the amount of time required between publishing a proposal and the start of voting.  The rules must be defined in the first message only, they cannot be redefined elsewhere in the message stream.  The software will reject any HCS message stream that does not place this configuration message as the first message (serial number 1).

Different propositions will be distinguished within this single topic by a unique ballot identifier.  This identifer will be the consensus timestamp corresponding to the `create-ballot` message defining the proposal ballot.  The software will also validate propositions against the HCS Voting Stream configuration rules.  In order to be valid, a proposition must adhere to the global minimum configuration properites and be submitted by account holders residing on the ballot create white-list (if specified).

### HCS JSON Messages

There are 3 message types

1. `define-rules`
2. `create-ballot`
3. `cast-vote`

Below are example JSON for each message type

#### Rules Definition Message
```json
{
	"type": "define-rules",
	"title": "TCG ⸱ $CLXY",
	"description": "The Creator's Galaxy Governance Voting Stream",
	"tokenId": "0.0.859814",
	"minVotingThreshold": 0.1,
	"ineligibleAccounts": [
		"0.0.849428", "0.0.859877", "0.0.859897", "0.0.859903", 
		"0.0.859906", "0.0.859908", "0.0.859910", "0.0.859911"
	],
	"ballotCreators": ["0.0.1386458"],
	"minimumVotingPeriod": 7,
	"minimumStandoffPeriod": 0
}
```

#### Create Ballot Message
```json
{
	"type": "create-ballot",
	"tokenId": "0.0.859814",
	"title": "CGIP-4 Community Governance & Voting Model",
	"description": "https://github.com/.../cgip-4.md",
	"discussion": "https://github.com/.../discussions",
	"scheme": "single-choice",
	"choices": ["Yes", "No", "Abstain"],
	"threshold": 0.5,
	"ineligible": ["0.0.1386458"],
	"startTimestamp": "1655323200.236702000",
	"endTimestamp": "1655928000.236702000",
}
```
The consensus timestamp for this message as recorded by the ledger will become the ballot identifier for this proposal.


#### Cast Vote message
```json
{
        "type": "cast-vote",
        "ballotId": "1655323200.236702000",
        "vote": 0,
}
```
If a single account casts multiple votes, only the last vote submitted during the voting window will be considered valid.  The weight of the vote will still be the $CLXY balance recorded at the opening of the voting window regardless of when the vote is cast.

## Backwards Compatibility

N/A

## Security Considerations

N/A

## How To Teach This

A network of Creators Galaxy participants use the Hedera Consensus Service (HCS) to maintain a registry of governance ballots, and the votes of the community on those ballots - creating an open, transparent, and auditable framework for goverining the evolution of the ecosystem.

## Reference Implementation

An open source implementation is available at [/the-creators-galaxy/hcs-governance](https://github.com/the-creators-galaxy/hcs-governance).

## Rejected Ideas

1. using memo fields within CryptoTransfers to cast votes on ballots
2. unique HCS topics for individual propositions

## Open Issues

1. Alternative vote weighting models, e.g. quadratic, per account, etc
2. How to best support other communities being able to leverage the framework, perhaps an environment config file that other communities/DAOs could easily define their "gov admin acct IDs", mirror node APIs, token IDs, etc

## References 

[snapshot.org](snapshot.org)

[Hedera's documentation](https://docs.hedera.com)

[The Creators Galaxy Whitepaper](http://creatorsgalaxyfoundation.com/whitepaper.pdf)

## Copyright

N/A
