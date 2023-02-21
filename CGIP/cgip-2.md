# CGIP-2: Community Governance & Voting Model

---

* cgip: 2
* title: Community Governance & Voting Model
* author: Campbell Law
* type: Standards Track
* category: Core
* status: Final
* created: 2023-2-21
* discussions-to: https://discussions.creatorsgalaxyfoundation.com/t/cgip-2-community-governance-voting-model/19
* updated: na
* requires: na
* replaces: na
* Superseded-by: na

---

# Abstract

The Creator’s Galaxy is a community-governed social ecosystem. This CGIP-2 proposes a voting framework for The Creator’s Galaxy DAO outlined in “CGIP-1: The Creator’s Galaxy DAO & The Creator’s Galaxy Improvement Process'' by which community members can propose features, economics and enhancements of The Creator’s Galaxy protocol, subsequently cast their votes on those proposals, and thereby directly influence its evolution. This CGIP-2 should be reviewed and considered in conjunction with CGIP-1, which has been simultaneously posted at [CGIP-1 link](https://discussions.creatorsgalaxyfoundation.com/t/cgip-1-the-creator-s-galaxy-dao-the-creator-s-galaxy-improvement-proposal-process/18).

# Motivation

The vision of The Creator’s Galaxy is that the community of creators, users, and applications will govern its evolution. This CGIP proposes a framework by which participants of the community can propose new features or enhancements, and by which the broader community can vote either in favor or against such CGIP - with their vote weighted by the number of $CLXY held.

# Rationale

The governance architecture uses [Hedera Consensus Service](https://docs.hedera.com/hedera/tutorials/consensus-service) (HCS) to provide an open, transparent and provable repository/database of propositions, votes, and ballot results. As the governance topic has no [submission keys](https://docs.hedera.com/hedera/sdks-and-apis/sdks/consensus-service/create-a-topic), subject to optional constraints defined in a HCS topic (as described below), anyone can both submit a CGIP and/or vote on one. As the HCS messages are archived on 3rd party mirror nodes, the history of CGIPs and votes is public and auditable.

The Creator’s Galaxy protocol will be the first ecosystem to leverage this framework for its own governance but the model is designed such that it could be adopted by other decentralized communities on Hedera.

# User Stories

Proposers

1.	A Proposer wants to create a new CGIP on which the community will vote
2.	Proposer visits [https://vote.creatorsgalaxyfoundation.com/](https://vote.creatorsgalaxyfoundation.com/), an IPFS CID, or runs the software locally, and indicates they wish to create a new proposition
3.	Proposer provides necessary information to describe the CGIP and details of the ballot
4.	Proposer signs HCS transaction to submit the proposition
5.	Community is notified of the new proposition and its upcoming ballot details

Voters

1.	A Voter becomes aware of a new CGIP and decides they wish to vote on it
2.	When the ballot opens, Voter visits [https://vote.creatorsgalaxyfoundation.com/](https://vote.creatorsgalaxyfoundation.com/), an IPFS CID, or runs the database locally, and finds the CGIP.
3.	Voter researches the previous discussions on the CGIP.
4.	Voter signs an HCS message to cast their vote on the CGIP.

# Specifications

The following sections describe the CGIP voting framework

## High Level

The voting process will allow community members to cast votes on CGIPs, these votes weighted by their $CLXY balances.

The sequence of steps for any particular CGIP is laid out in more detail in CGIP-1.

1.	Submitting a Live CGIP will result in:
	* Community members being informed of the Live CGIP via multiple channels (e.g. Discord, Twitter, etc.)
	* An HCS message will be submitted to an HCS Topic (as laid out in more detail below) to record the above Live CGIP terms with a `create-ballot` message. The HCS message’s consensus timestamp becomes the identifier for the Live CGIP.
2.	Members of the ecosystem, having subscribed to the above topic or receiving notification via other channels (e.g. Twitter, Discord, in app, etc), will be made aware of the upcoming vote of the Live CGIP.
3.	For the purposes of weighted voting, the account holder’s $CLXY balance at the moment in time which the voting window opens is considered the weighted snapshot balance for that account holder. Hedera Mirror nodes provide the balances of accounts at any time in history, and will be queried for this information when tabulating vote results.
4.	The global configuration and/or individual ballot rules may identify accounts that may not be permitted to vote on a CGIP. The balances of these accounts will not be included when computing any required threshold quorum requirements.
5.	For the duration of the CGIP voting window, members of the community can submit votes as cast-vote messages against the above topic. These vote messages will indicate the CGIP identifier. These vote transactions will be signed by the private key(s) of the relevant Hedera account. If an account submits multiple cast-vote messages within the voting window for a given CGIP, only the last will be counted.
6.	Members of the community may host instances of the hcs-governance open source software to help facilitate access to the voting process.
7.	The voting window will remain open for at least the minimum requirement specified in the HCS topic configuration, and may be lengthened further by the CGIP author. After the voting window closes, each vote will be weighted according to the $CLXY balance of the corresponding Hedera account at the time of the voting window opening.
8.	The results of the ballot will be tallied and displayed by various software systems that can be both hosted and run independently by anyone wishing to validate the voting systems results.

## Vote weighting

The votes of community members will be weighted by the amount of $CLXY held within their respective Hedera accounts. Initially, the only weighting model supported will be '1 $CLXY = 1 vote', and a minimum of 10% of the tokens circulating supply will be needed to achieve quorum. 

An account's voting weight will be the $CLXY balance across all Hedera accounts at the time when the respective ballot opens for voting.

Both the global configuration and ballot definitions may list accounts that are not permitted to vote. Their weighted $CLXY balance will not be taken into account when computing any required quorum threshold.

$CLXY holders voting abstain will be counted as having voted for quorum computation purposes.

The Hedera Mirror REST API provides a call to retrieve the balance of all accounts that hold $CLXY at a given point in time is similar to the following:

`/api/v1/tokens/0.0.859814/balances?account.balance=gt:0&order=asc&timestamp=gte:[insert ballot id here]`

## HCS Topics

All governance messages (CGIP creation & votes) will be submitted to a single HCS governance topic.

There will be no restrictions on who can submit messages to this HCS topic. However, certain accounts may be designated as curators, and only CGIPs submitted by these accounts will be considered valid.

The topic will be immutable.

The first message in the HCS topic shall be a `define-rules` message outlining the global configuration. The information in this first message may include the white-list of accounts that may submit CGIPs, a global list of accounts that may not vote on any CGIP, the minimum time required for voting windows, and the amount of time required between publishing a CGIP and the start of voting. The rules must be defined in the first message only and cannot be redefined elsewhere in the message stream. The software will reject any HCS message stream that does not place this configuration message as the first message (serial number 1).

Different CGIPs will be distinguished within this single topic by a unique ballot identifier. This identifier will be the consensus timestamp corresponding to the `create-ballot` message defining the CGIP ballot. The software will also validate create-ballot messages against the global configuration rules. In order to be valid, a proposition must adhere to the global minimum configuration properties and be submitted by account holders residing on the ballot create enabled-list (if specified).

## HCS JSON Messages

There are 3 message types
1.	define-rules
2.	create-ballot
3.	cast-vote

Below are example JSON for each message type

## Rules Definition Message
```
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

## Create Ballot Message
```
{
	"type": "create-ballot",
	"tokenId": "0.0.859814",
	"title": "CGIP-2 Community Governance & Voting Model",
	"description": "https://github.com/.../cgip-4.md",
	"discussion": "https://github.com/.../discussions",
	"scheme": "single-choice",
	"choices": ["Yes", "No"],
"threshold": 0.1,
	"ineligible": ["0.0.1386458"],
	"startTimestamp": "1655323200.236702000",
	"endTimestamp": "1655928000.236702000",
}
```

The consensus timestamp for this message as recorded by the ledger will become the ballot identifier for this CGIP.

## Cast Vote message
```
{
        "type": "cast-vote",
        "ballotId": "1655323200.236702000",
        "vote": 0,
}
```

If a single account casts multiple votes, only the last vote submitted during the voting window will be considered valid. The weight of the vote will still be the $CLXY balance recorded at the opening of the voting window regardless of when the vote is cast.

## Steps to Implement

All required steps have been taken, pending The Creator’s Galaxy DAO approving this CGIP-2.

Upon approval of this CGIP-2, the voting protocol and processes as described herein will be deemed to be the voting protocol and process for governance of The Creator’s Galaxy protocol.

# How To Teach This

A network of The Creator’s Galaxy ecosystem participants uses the Hedera Consensus Service (HCS) to maintain a registry of governance ballots, and the votes of the community on those ballots - creating an open, transparent, and auditable framework for governing the evolution of the ecosystem.

# Reference Implementation

An open source implementation is available at [/the-creators-galaxy/hcs-governance](https://github.com/the-creators-galaxy/hcs-governance).

# Rejected Ideas

1.	using memo fields within CryptoTransfers to cast votes on ballots
2.	unique HCS topics for individual CGIPs

# Open Issues

1.	Alternative vote weighting models, e.g. quadratic, per account, etc
2.	Flexibility in ballot durations
3.	Should certain accounts be excluded from voting? or otherwise have their influence diminished?
4.	How to best support other communities being able to leverage the framework, perhaps an environment config file that other communities/DAOs could easily define their "gov admin acct IDs", mirror node APIs, token IDs, etc

# References

* [Hedera's documentation](https://docs.hedera.com/hedera/)
* [The Creators Galaxy Whitepaper](https://www.creatorsgalaxyfoundation.com/whitepaper.pdf)

# Copyright

N/A