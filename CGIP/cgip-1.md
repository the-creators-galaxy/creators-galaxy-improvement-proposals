- cgip: 1
- title: Creators Galaxy Improvement Proposal Process
- author: Paul Madsen (@paulatcalaxy)
- type: Process
- status: Draft
- created: 2021-11-11
- discussions-to: 
- updated: 2021-11-11

## What is a CGIP?

CGIP stands for Creator's Galaxy Improvement Proposal. These are design documents that inform The Creator's Galaxy community, 
about new features on The Creator's Galaxy or changes to the ecosystem’s structure, processes, or environment.

CGIPs are designed to provide both precise technical specifications of a new feature and rationale for adopting it. Whoever creates a CGIP is responsible for persuading and convincing others in the community and building consensus around the new proposal.

A CGIP should be technically clear and concise. CGIPs should be as granular as possible. Small targeted CGIPs are more likely to reach consensus and result in a reference implementation. 

CGIPs are intended to be the primary mechanism for proposing new features, for collecting community input, and for documenting the design decisions that have gone
into the Creators Galaxy.

Because the CGIPs are maintained as text files in a versioned repository, their revision history is the historical record of the feature proposal and associated discussion.

It is the expectation and plan that the CGIP process, and the governance that it enables, will become more and more decentralized over time. Particularly, in that decisions on CGIP approval (by which governance manifests) will be influenced by holdings of $CLXY tokens.

## CGIP Types

There are three kinds of CGIP:

1. A **Standards Track** CGIP describes a new feature or implementation for The Creator's Galaxy.

    **a. Core:** Core CGIPs propose changes to the technical architecture and implementations that underly applications within The Creator's Galaxy, including how the services that Hedera, or other distributed ledgers, offer are to be leveraged.

    **b. Economics:** Economics CGIPs propose changes to the economics of The Creator's Galaxy, including how the $CLXY token is used, or how fees are allocated.
    
    **d. Governance:** Governance CGIPS propose changes to how The Creator's Galaxy is governed, including how members of the community can influence the progression of the ecosystem.

2. An **Informational** CGIP provides general guidelines or information to the community, but does not propose a new feature. 

3. A **Process** CGIP describes a process surrounding The Creator's Galaxy, or proposes a change to a process. This CGIP is a Process CGIP as it defines the process by which CGIPs are created and discussed.

## CGIP Status 
* Idea - An idea that is pre-draft. This is not tracked within the CGIP Repository.
* Draft - The first formally tracked stage of a CGIP in development. A CGIP is merged by a CGIP Editor into the repository when properly formatted. A draft CGIP is open for consideration and is undergoing rapid iteration and changes.
* Review - A CGIP Author marks an CGIP as ready for and requesting Peer Review.
* Final - This CGIP represents the final standard. A Final CGIP exists in a state of finality and should only be updated to correct errata and add non-normative clarifications.
* Withdrawn - The CGIP Author(s) have withdrawn the proposed CGIP. This state has finality and can no longer be resurrected using this CGIP number. If the idea is pursued at later date it is considered a new proposal.
* Living - A special status for CGIPs that are designed to be continually updated and not reach a state of finality. This includes this CGIP, CGIP-1.

## CGIP Participants
The following actors in the Creators Galaxy may participate in the CGIP process, either proposing, reviewing, or deciding on CGIPs

1. The Creators Galaxy Foundation's primary focus is helping manage the open-source software standards and specifications that power applications in The Creator’s Galaxy, helping oversee the ecosystem’s decentralized governance.

2. The Creators Council is comprised up to 20 notable Creators empowered to represent the Creators viewpoint in evolving the Creators Galaxy and helping ensure it's the go-to place for web3 personal monetization. The Council will provide direct insight and advice to The Creator’s Galaxy ecosystem by providing oversight into product features, roadmap, and general growth of the ecosystem. This insight and oversight will primarily manifest as review and feedback of CGIPs. 

3. Calaxy Inc. is building the first instance of an application within The Creator's Galaxy that adheres to the ecosystem specifications outlined in [The Creator's Galaxy Whitepaper](creatorsgalaxyfoundation.com/whitepaper).

4. 3rd party applications. The vision of the Creator's Galaxy is that there will be a broad and diverse ecosystem of applications empowering the future of
content creators, which can collectively participate within The Creator’s Galaxy. 3rd party applications are expected to be key participants in the CGIP process, both as conbtributors and reviewers.

5. Creator's Galaxy Community members can propose new CGIPs and comment on others. Those community members that hold $CLXY tokens will be able to use those tokens when voting on decisions on CGIPs.

## Parts of a CGIP

Each CGIP should have the following parts/sections:

1. Preamble -- RFC 822 style headers containing meta-data about the CGIP, including the CGIP number, a short descriptive title (limited to a maximum of 44 characters), the names and, optionally, the contact info for each author, etc.

2. Abstract -- a short (~200 word) description of the technical issue being addressed.

3. Motivation -- The motivation should clearly explain why the existing specification is inadequate to address the problem that the CGIP solves. 

4. Rationale -- The rationale fleshes out the specification by describing why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages.

5. User stories -- Provide a list of "user stories" to express how this feature, functionality, improvement, or tool will be used by the end user - whether that be fans or Creators within the ecosystem. 

6. Specification -- The technical specification should describe the syntax and semantics of any new features. The specification should be detailed enough to allow competing, interoperable implementations (for at least the current Hedera ecosystem, but ideally, all web3 ecosystems).

7. Backwards Compatibility -- All CGIPs that introduce backward incompatibilities must include a section describing these incompatibilities and their severity. 

8. Security Implications -- If there are security concerns in relation to the CGIP, those concerns should be explicitly addressed to make sure reviewers of the CGIP are aware of them.

9. How to Teach This -- For a CGIP that adds new functionality or changes interface behaviors, it is helpful to include a section on how to teach users, new and experienced, about the new feature.

10. Reference Implementation -- The reference implementation must be complete before any CGIP is given the status of “Final”. The final implementation must include test code and documentation.

11. Rejected Ideas -- Throughout the discussion of a CGIP, various ideas will be proposed which are not accepted. Those rejected ideas should be recorded along with the reasoning as to why they were rejected. This both helps record the thought process behind the final version of the CGIP as well as preventing people from bringing up the same rejected idea again in subsequent discussions.

    In a way, this section can be thought of as a breakout section of the Rationale section that focuses specifically on why certain ideas were not ultimately pursued.

12. Open Issues -- While a CGIP is in draft, ideas can come up which warrant further discussion. Those ideas should be recorded so people know that they are being thought about but do not have a concrete resolution. This helps make sure all issues required for the CGIP to be ready for consideration are complete and reduces people duplicating prior discussions.

13. References -- A collections of URLs used as references through the CGIP.

14. Copyright/license -- Each new CGIP must be placed under the Apache License, Version 2.0 -- see [LICENSE](../LICENSE) or (https://www.apache.org/licenses/LICENSE-2.0)

## CGIP Workflow

???????

## CGIP Formats and Templates

CGIPs should be written in markdown format. There is a template to follow.

### CGIP Header Preamble

Each CGIP must begin with a header preamble in list format. The headers must appear in the following order. Headers marked with “*” are optional and are described below. All other headers are required.

- cgip: CGIP number
- title: CGIP title
- author: a list of the author’s or authors’ name(s) and/or username(s), or name(s) and email(s).
- type: <Standards Track | Informational | Process>
- \* category: <Core | Governance | Economics >
- status: < >
- created: date created on
- \* discussions-to: a URL pointing to the official discussion thread
- \* updated: comma separated list of dates
- \* requires: CGIP number(s)
- \* replaces: CGP number(s)
- \* superseded-by: CGIP number(s)

#### `author` header

The author header lists the names, email addresses or GitHub usernames of the authors/owners of the CGIP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the author header value must be:

Random J. User <address@dom.ain>

or

Random J. User (@username)

if the email address or GitHub username is included, and Random J. User

if email or username are not given.

At least one author must use a GitHub username in order to be notified on change requests and have the capability to approve or reject them.

#### `discussions-to` header

While a CGIP is a draft, a discussions-to header will indicate the URL where the CGIP is being discussed. Examples of places to discuss your CGIP include an issue in this repo or in a fork of this repo, the Hedera Developer Discord, or Reddit r/hashgraph.

No discussions-to header is necessary if the CGIP is being discussed privately with the author.

As a single exception, discussions-to cannot point to GitHub pull requests.

#### `type` header

The Type header specifies the type of CGIP: Standards Track, Informational, or Process. If the track is Standards, the CGIP must include the category header.

#### `category` header

The category header specifies the CGIP category (Core, Economics, Governance). This is required for Standard Track CGIPs only.

#### `created` header

The created header records the date that the CGIP was assigned a number. This header should be in ISO 8601 format (yyyy-mm-dd), e.g. 2019-09-16.

#### `updated` header

The updated header records the date(s) when the CGIP was updated with “substantial” changes. The header is only valid for CGIPs of Draft and Active status. This header should be in ISO 8601 format (yyyy-mm-dd), e.g. 2019-09-16.

#### `requires` header

CGIPs may have a requires header, indicating the CGIP numbers that this CGIP depends on.

#### `superseded-by` and `replaces` headers

CGIPs may also have a superseded-by header indicating that a CGIP has been rendered obsolete by a later document; the value is the number of the CGIP that replaces the current document. The current document must change status to “Replaced” once the superseding CGIP is changed to “Final” status. The newer CGIP must have a replaces header containing the number of the CGIP that it rendered obsolete.

### Linking to other CGIPs

References to other CGIPs should follow the format CGIP-N where N is the CGIP number you are referring to. Each CGIP that is referenced in an CGIP MUST be accompanied by a relative markdown link the first time it is referenced, and MAY be accompanied by a link on subsequent references. The link MUST always be done via relative paths so that the links work in this GitHub repository, forks of this repository, the main CGIPs site, mirrors of the main CGIP site, etc. For example, you would link to this CGIP with [CGIP-1](./cgip-1.md).

### Auxiliary Files

Images, diagrams, and auxiliary files should be included in a subdirectory of the assets folder for that CGIP as follows: assets/cgip-N (where N is to be replaced with the CGIP number). When linking to an image in the CGIP, use relative links such as ../assets/cgip-1/image.png.


## Copyright
This document is licensed under the Apache License, Version 2.0 -- see [LICENSE](../LICENSE) or (https://www.apache.org/licenses/LICENSE-2.0)
