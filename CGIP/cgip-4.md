- cgip: 4
- title: Community Governance & Voting Model
- author: @paulatcalaxy
- type: Standards Track 
- category: Core 
- status: < >
- created: January 15/2022
- discussions-to: 
- updated: 
- requires: na
- replaces: na
- superseded-by: 

## Abstract

The Creator’s Galaxy is a community-governed social ecosystem. This specification describes a framework by which community members can propose features, economics and enhancements of the ecosystem, subsequently cast their votes on those propositions, and thereby directly influence its evolution. We believe that this framework and the corresponding open source software could be adopted by other communities in the Hedera ecosystem and leveraged for their own governance decisions and as such, contribute to the development of DAOs on Hedera.

## Motivation

The vision of the Creator’s Galaxy is that the community of Creators, Fans, and applications will govern its evolution. This CGIP proposes a framework by which arbitrary members of the community can propose new features or enhancements, and by which the broader community can vote either in favor or against that proposition - with their vote weighted by the number of $CLXY coins they own.

## Rationale

The governance architecture uses [Hedera Consensus Service](https://docs.hedera.com/guides/docs/sdks/consensus) to provide an open, transparent and provable repository/database of propositions, votes, and ballot results. As the governance topic has no [submission keys](https://docs.hedera.com/guides/docs/sdks/consensus/create-a-topic), anyone can both submit a proposition and/or vote on one. As the HCS messages are archived on 3rd party mirror nodes, the history of propositions and votes is public and auditable.

The Creator's Galaxy will be the first ecosystem to leverage this framework for its own governance but the model is designed such that it could be adopted by other decentralized communities on Hedera.

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
2. After sufficient discussion, a member of the community will visit gov.creatorsgalaxy.com to create a proposition. Note: the codebase being deployed at gov.creators.galaxy.com will also be available to be ran locally. Further, each version should be distributed via IPFS, and accessible through it's unique CID, to ensure it's accessibility in the future. They will describe the feature or issue, link to previous CGIP discussions, and specify a start time for the ballot at least 24 hours in the future. 
3. Submitting the proposition will result in:
* community members will be informed of the proposition and details of the upcoming ballot via multiple channels (e.g. Discord, Twitter, in app, etc)
* an HCS message will be submitted to an HCS Topic to record the above ballot terms with a `CreateBallot` message. Each ballot will have a unique identifier. The proposer will sign the HCS message.
4. Members of the ecosystem, having subscribed to the above topic or receiving notification via other channels (e.g. Twitter, Discord, in app, etc), will be made aware of the upcoming ballot
5. 24 hours before the stipulated start of the ballot, a snapshot of $CLXY balances across Hedera accounts will be automatically taken. This snapshot will be auditable and made available to the community. The snapshot will be a list of all Hedera accounts holding $CLXY and the corresponding balances at that point in time.
6. The snapshot will be bound to the ballot with a HCS `AddSnapshot` message. The $CLXY balances will weight votes submitted on the ballot.
7. For the duration of the ballot, members of the community can submit votes as `VoteOnBallot` messages against the above topic. These vote messages will indicate the Ballot identifier. These votes transactions will be signed by the private key of the relevant Hedera account. if an account submits multiple `VoteOnBallot` messages for a given ballot, only the last will be considered valid.
8. Members of the community will collect and validate the voting messages during the period of the ballot.
9. The ballot will close 7 days after opening. At that time, each vote will be weighted according to the $CLXY balance of the corresponding Hedera account, as determined by the snapshot.
10. The results of the ballot will be calculated and recorded via HCS `ReportBallotResults` message, and annnounced to the commiunity via other channels.


### Snapshot mechanism

The votes of community members will be weighted by the amount of $CLXY they own within their Hedera account. Initially, the only weighting model supported will be '1 $CLXY = 1 vote'

A snapshot of $CLXY balance across all Hedera accounts will be taken just before a ballot opens for voting.

The Hedera Mirror REST API provides a call to retrieve the balance of all accounts that hold a particular token

```
/api/v1/tokens/<clxy token_id>/balances?order=asc
```

Once the balances are retrieved, the JSON will be validated against another Hedera Mirror Node, and then distributed on IPFS.

A link to the above storage location and hash will be sent as part of the `AddSnapshot` HCS message.

A valid `AddSnapshot` message must be sent from a previously established & authorized, publicly known Hedera account, e.g. : 0.0.123456, where 0.0.123456 is a multisig account. 

### HCS Topics

All governance messages (ballot management & votes) will be submitted against a single HCS governance topic.

There will be no restrictions on who can submit against this topic.

The topic will be immutable.

Different propositions will be distinguished within this single topic by a unique ballot identifier.

### HCS JSON Messages

There are 4 distinct message types

1. CreateBallot
2. AddSnapshot
3. VoteOnBallot
4. ReportBallotResults

Below are example JSON for each message type

#### CreateBallot Message
```
{
  "ballotId": "{{ ballotId }}",
  "title": "Ballot title",
  "description": "Ballot description",
  "discussion": "link to CGIP",
  "startTimestamp": "",
  "endTimestamp": ""
}
```
Only the first `CreateBallot' message with a given ballot identifier will be considered valid.

#### AddSnapsot message
```
{
  "ballotId": "{{ ballotId }}",
  “snapshot” : {snapshot}
}
```
An `AddSnapshot` message will only be considered valid if sent from the previously established multi-sig governance account.

#### VoteOnBallot message
```
{
  "ballotId": "{{ ballotId }}",
  “vote” : {A}
}
```
If a single account casts multiple votes, only the last vote will be considered valid.

#### ReportBallotResults message
```
{
  "ballotId": "{{ ballotId }}",
   “result” : {A}
}
```
A `ReportBallotResults` message will only be considered valid if sent from the previously established multi-sig governance account.


## Backwards Compatibility

N/A

## Security Considerations

N/A

## How To Teach This

A network of Creators Galaxy participants use the Hedera Consensus Service (HCS) to maintain a registry of governance ballots, and the votes of the community on those ballots - creating an open, transparent, and auditable framework for goverining the evolution of the ecosystem.

## Reference Implementation

An open source implementation is under development, and coming soon.

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
