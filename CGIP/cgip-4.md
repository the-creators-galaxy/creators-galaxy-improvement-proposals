- cgip: 4
- title: Community Governance & Voting Model
- author: @paulatcalaxy
- type: Standards Track 
- category: Core 
- status: Last Call
- created: January 15/2022
- discussions-to: 
- updated: June 15/2022
- requires: na
- replaces: na
- superseded-by: 

## Abstract

The Creator’s Galaxy is a community-governed social ecosystem. This specification describes a framework by which community members can propose features, economics and enhancements of the ecosystem, subsequently cast their votes on those propositions, and thereby directly influence its evolution. We believe that this framework and the corresponding open source software could be adopted by other communities in the Hedera ecosystem and leveraged for their own governance decisions and as such, contribute to the development of DAOs on Hedera.

## Motivation

The vision of the Creator’s Galaxy is that the community of Creators, Members, and applications will govern its evolution. This CGIP proposes a framework by which arbitrary participants of the community can propose new features or enhancements, and by which the broader community can vote either in favor or against that proposition - with their vote weighted by the number of $CLXY coins they own.

## Rationale

The governance architecture uses [Hedera Consensus Service](https://docs.hedera.com/guides/docs/sdks/consensus) to provide an open, transparent and provable repository/database of propositions, votes, and ballot results. As the governance topic has no [submission keys](https://docs.hedera.com/guides/docs/sdks/consensus/create-a-topic), anyone can both submit a proposition and/or vote on one. As the HCS messages are archived on 3rd party mirror nodes, the history of propositions and votes is public and auditable.

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
6. Scrutineer sends HCS message to report ballot result

## Specification

The following sections describe the proposition ballot framework

### High Level 

The voting process will allow community members to cast votes on governance ballots, these votes weighted by their $CLXY balances.

At high-level, the sequence of steps for a particular governance proposition is

1. The community will use the CGIP process to discuss an issue. 
2. After sufficient discussion, a member of the community will visit gov.creatorsgalaxy.com to create a proposition. Note: the codebase being deployed at gov.creators.galaxy.com will also be available to be run locally. Further, each version should be distributed via IPFS, and accessible through it’s unique CID, to ensure it’s accessibility in the future. They will describe the feature or issue, link to previous CGIP discussions, and specify a start time for the ballot at least 24 hours in the future. 
3. Submitting the proposition will result in:
	* Community members will be informed of the proposition and details of the upcoming ballot via multiple channels (e.g. Discord, Twitter, in app, etc)
	* An HCS message will be submitted to an HCS Topic to record the above ballot terms with a `create-ballot` message. The HCS message’s consensus timestamp becomes the identifier for the proposal, and the account signing the transaction submitting the HCS message becomes the proposal’s author.
4. Members of the ecosystem, having subscribed to the above topic or receiving notification via other channels (e.g. Twitter, Discord, in app, etc), will be made aware of the upcoming ballot
5. For the purposes of weighted voting, the account holder’s $CLXY balance at the moment in time which the voting window opens is considered the weighted snapshot balance for that account holder.  Hedera Mirror nodes provide the balances of accounts at any time in history, and will be queried for this information when tabulating vote results.
6. For the duration of the proposal voting window, members of the community can submit votes as `cast-vote` messages against the above topic. These vote messages will indicate the Ballot identifier. These votes transactions will be signed by the private key(s) of the relevant Hedera account. If an account submits multiple `cast-vote` messages within the voting window for a given ballot, only the last will be counted.
7. Members of the community will collect and validate the voting messages during the period of the ballot.
8. The ballot will close not earlier than 7 days after opening, this will otherwise be configurable by the proposal author. At that time, each vote will be weighted according to the $CLXY balance of the corresponding Hedera account at the time of the voting window opening.
9. The results of the ballot will be tallied and displayed by various software systems that can be both hosted and run independently by Scrutineers.


### Vote weighting

The votes of community members will be weighted by the amount of $CLXY they own within their Hedera account. Initially, the only weighting model supported will be '1 $CLXY = 1 vote'

An account's voting weight will be the $CLXY balance across all Hedera accounts at the time when the respective ballot opens for voting.

The Hedera Mirror REST API provides a call to retrieve the balance of all accounts that hold $CLXY at a given point in time is similar to the following:

```
/api/v1/tokens/0.0.859814/balances?account.balance=gt:0&order=asc&timestamp=gte:[insert ballot id here]
```

### HCS Topics

All governance messages (ballot creation & votes) will be submitted against a single HCS governance topic.

There will be no restrictions on who can submit against this topic.

The topic will be immutable.

Different propositions will be distinguished within this single topic by a unique ballot identifier.  This identifer will be the consensus timestamp corresponding to the `create-ballot` message defining the proposal ballot.

### HCS JSON Messages

There are 2 message types

1. `create-ballot`
2. `cast-vote`

Below are example JSON for each message type

#### Create Ballot Message
```json
{
	"type": "create-ballot",
	"tokenId": "0.0.859814",
	"title": "CGIP-4 Community Governance & Voting Model",
	"description": "https://github.com/.../cgip-4.md",
	"discussion": "https://github.com/.../discussions",
	"scheme": "single-choice",
	"choices": ["Yes", "No"],
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
2. Flexibility in ballot durations
3. Should certain accounts be excluded from voting? or otherwise have their influence diminished?
4. How to best support other communities being able to leverage the framework, perhaps an environment config file that other communities/DAOs could easily define their "gov admin acct IDs", mirror node APIs, token IDs, etc

## References 

[snapshot.org](snapshot.org)

[Hedera's documentation](https://docs.hedera.com)

[The Creators Galaxy Whitepaper](http://creatorsgalaxyfoundation.com/whitepaper.pdf)

## Copyright

N/A
