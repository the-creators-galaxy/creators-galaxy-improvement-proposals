CGIP-1: The Creator’s Galaxy DAO & The Creator’s Galaxy Improvement Proposal Process

---

* cgip: 1
* title: The Creator’s Galaxy DAO & The Creator’s Galaxy ( Improvement Proposal Process
author: Campbell Law
* type: Process
* status: Final
* created: 2023-2-21
* discussions-to: https://discussions.creatorsgalaxyfoundation.com/t/cgip-1-the-creator-s-galaxy-dao-the-creator-s-galaxy-improvement-proposal-process/18
* updated: N/A

---

# 1. Abstract
This document proposes the structure and governance of a DAO (decentralized autonomous organization) that would be governed by the holders of $CLXY, the decentralized governance token of The Creator’s Galaxy protocol and ecosystem, via CGIPs.

What is a CGIP? “CGIP” stands for “Creator's Galaxy Improvement Proposal”. These are documents that propose to The Creator's Galaxy community new features on The Creator's Galaxy protocol or changes to the ecosystem’s structure, processes, or environment. This CGIP, CGIP-1: The Creator’s Galaxy DAO & The Creator’s Galaxy Improvement Proposal Process, proposes the processes for community governance, including introducing The Creator’s Galaxy DAO.

# 2. Motivation

The Creator’s Galaxy Foundation is a Cayman Islands foundation company which will serve The Creator’s Galaxy DAO and be governed by it via CGIPs. The Creator’s Galaxy DAO will have the ability to submit proposals, deliberate and vote and make such proposals and ideas a reality.

The goal of CGIPs is to ensure that the community determines the future of The Creator’s Galaxy ecosystem, and has a clear, easy to use process for doing so.

The guiding values of The Creator’s Galaxy Foundation are:

1.	Integrity - Never take shortcuts, even if that means progress comes slower than desired
2.	Equality Meets Equity - Our greatest contribution will always be measured by our commitment to improving the lives of entertainers everywhere
3.	Transparency - Proposals and their outcomes are visible to all stakeholders within The Creator’s Galaxy
4.	Innovation - Tomorrow's tools, available today
5.	Inclusion – The Creator’s Galaxy vows to build an ecosystem that benefits content creators of all types

# 3. Rationale

The Creator’s Galaxy Foundation serves The Creator’s Galaxy DAO in fostering and empowering a community of creators and users contributing to and developing The Creator’s Galaxy ecosystem. To achieve these goals, it is essential to establish a clear governance system to effectuate the desires and decisions of The Creator’s Galaxy DAO via the submission, voting and implementation of CGIPs.

## Guidelines

-	CGIPs are designed to provide both precise specifications or descriptions of a new feature and rationale for The Creator’s Galaxy DAO to adopt them. 
-	Whoever creates a CGIP is responsible for persuading and convincing others in the community and building consensus around the new proposal. 
-	A CGIP should be technically clear and concise, and as granular as possible. Small targeted CGIPs are more likely to reach consensus and result in a reference implementation. 

CGIPs are intended to be the primary mechanism for proposing new features, for collecting community input, and for documenting the design decisions that have gone into The Creator’s Galaxy protocol. Because CGIPs are maintained as text files in a versioned repository, their revision history is the historical record of the feature proposal and associated discussion. It is the expectation and plan that the CGIP process, and the governance that it enables, will become more and more decentralized over time. 

# 4. Specifications

## 4.1. Types of proposals

There are four kinds of Creator’s Galaxy Improvement Proposals:

1. **A Standards Track** CGIP describes a new feature or implementation for The Creator's Galaxy. There are three sub-categories of a Standards Track CGIP:

    a. **Core**: Core CGIPs propose changes to the technical architecture and implementations that underlie applications within The Creator's Galaxy protocol, including how the services that Hedera, or other distributed ledgers, offer are to be leveraged.

    b. **Economics**: Economics CGIPs propose changes to the economics of The Creator's Galaxy protocol, including how the $CLXY token is used, or how fees are allocated.
    
    c. **Governance**: Governance CGIPs propose changes to how The Creator's Galaxy protocol is governed, including how members of the community can influence the progression of the ecosystem.

2. A **Grants** CGIP is purposely used when requesting grant funding of $CLXY tokens. Notably this differs from a **Standard - Economics** type of CGIPs as those are intended to change how $CLXY is utilized within the network’s on-chain fees outside of grant funding.

3. An **Informational** CGIP provides general guidelines or information to the community, but does not propose a new feature. 

4. A **Process** CGIP describes a process surrounding The Creator's Galaxy protocol, or proposes a change to a process. This CGIP-1 is a Process CGIP as it defines the process by which CGIPs are created and discussed. This can include updates to CGIP-1 & CGIP-2: Community Governance & Voting Model.

## 4.2. Status Types of Proposals  

1.	**Idea** - An idea that is pre-draft.
2.	**Draft** - The first formally tracked stage of a CGIP in development. A CGIP is merged by a CGIP Editor (a community member appointed by the Stewards Council) into a repository when properly formatted. Members of the Stewards Council will by default be CGIP Editors. A Draft CGIP is open for consideration and is undergoing rapid iteration and changes.
3.	**Review** - The author of the CGIP (“CGIP Author”) marks a CGIP as ready for and requesting Stewards Council Review.
4.	**Live** - A CGIP moves into this status when it is live for voting by the community.
5.	**Final** - This CGIP represents the final standard. A Final CGIP exists in a state of finality and should only be updated to correct errata and add non-normative clarifications.
6.	**Withdrawn** - The CGIP Author(s) have withdrawn the proposed CGIP. This state has finality and can no longer be resurrected using the prior CGIP number. If the idea is pursued at a later date it is considered a new proposal.

## 4.3. Defining participants 

The following actors in The Creator’s Galaxy may participate in the CGIP process, either by proposing, reviewing, voting and/or implementing CGIPs.

1. The Creator’s Galaxy Foundation's primary focus is helping govern the open-source software standards and specifications that power applications in The Creator’s Galaxy protocol, helping oversee the ecosystem’s decentralized governance. 

2. 3rd party applications. The vision of The Creator's Galaxy protocol is that there will be a broad and diverse ecosystem of applications empowering the future of content creators, which can collectively participate within The Creator’s Galaxy ecosystem. These various 3rd party applications are expected to be key participants in the CGIP process as community members and contributors.

3. The Creator’s Galaxy DAO. Any community member can propose new CGIPs and comment on others. Those community members that hold $CLXY tokens will be able to use those tokens when voting on decisions on CGIPs. There will be a community nominated group of at least 5 individuals comprising the Stewards Council who manage a set of multisig wallets on behalf of The Creator’s Galaxy DAO and The Creator’s Galaxy Foundation. The details of the DAO are outlined in Section 4.5 below. 

## 4.4. CGIP Workflow

These are the clearly defined, step-by-step phases a CGIP must go through in order to be fully implemented. 

**Phase 1 - CGIP Idea**

An idea must be created within the discussions section of [Discourse (https://discussions.creatorsgalaxyfoundation.com/)](https://discussions.creatorsgalaxyfoundation.com/) and receive confirmation from a CGIP Editor that the proposal complies with the DAO’s guidelines before moving onto Phase 2. The individual(s) who came up with the idea/proposal will become the CGIP’s author or authors. After receiving this confirmation from a CGIP Editor, the proposal would be moved to Phase 2.

Minimum duration of Phase 1: N/A

**Phase 2 - CGIP Draft**

Once a proposal idea has received confirmation from a CGIP Editor that it’s compliant with the DAO guidelines, the proposal should be updated to reflect its status as a CGIP Draft. This CGIP Draft should be added to Discourse in a format matching the template to be provided by The Creator’s Galaxy Foundation as laid out in Section 4.7 of this CGIP-1. 

This draft must be available for a minimum of 14 days for comments from the community. After the 14 day minimum window, the CGIP Author(s) can decide whether or not they believe the CGIP Draft has gained enough response and support from the community to move to Phase 3. 

Moving a CGIP Draft to Phase 3 is done by updating the draft, and informing both a CGIP Editor, and a member of the Stewards Council by tagging them in the discussion post on Discourse for all the community to see. If the CGIP Author and members of the community do not participate in the discussion for 30 days, it will be automatically rejected for failing to make progress. 

Minimum duration of Phase 2: 14 days.

**Phase 3 - Stewards Council Review**

During this phase, the CGIP Draft will be reviewed by the current Stewards Council members. The goal of this phase is to ensure the technical and legal feasibility of implementing the proposal as drafted. It can be expected that this phase will take a minimum of 7 days to complete, but perhaps longer depending on the proposal’s requirements.

The Stewards Council will review each CGIP Draft to ensure that such CGIPs: 
-	Are technically feasible; 
-	Include all required proposal terms and specific and granular details regarding the implementation of the CGIP;
-	Do not directly conflict with another CGIP currently up for vote or CGIP previously approved by The Creator’s Galaxy DAO;
-	Do not otherwise violate The Creator’s Galaxy Foundation’s bylaws or articles, any statutory requirements of Cayman Islands laws or the laws or regulations of any other applicable jurisdiction;

If the CGIP Draft is approved by the Stewards Council, they or a CGIP Editor will move it to Phase 4. This is done by creating an instance on The Creator’s Galaxy voting [website (https://vote.creatorsgalaxyfoundation.com/)](https://vote.creatorsgalaxyfoundation.com/), and as outlined in Phase 4 below.  

If the proposal fails to meet the Stewards Council requirements, they will move the proposal back to Phase 2 with comments as to why it failed to pass beyond this phase. 

Minimum duration of Phase 3: 7 days.

**Phase 4 - Live CGIP**

When a CGIP enters Phase 4, it will be added to [https://vote.creatorsgalaxyfoundation.com/](https://vote.creatorsgalaxyfoundation.com/) by a CGIP Editor or member of the Stewards Council. Its voting window will begin 7 days after the proposal has been added, and will be live (open for voting) for 7 days.  

The voting options will be “Yes” in support of the proposal, “No” not in support of the proposal, or “Abstain” which implies that a voter wishes to contribute to the proposal’s minimum voting threshold without influencing the community. After the 7 days of voting has completed (14 days in total for Phase 4), the results will be visible on [https://vote.creatorsgalaxyfoundation.com/](https://vote.creatorsgalaxyfoundation.com/), and the proposal will move to Phase 5.

Duration of Phase 4: 14 days.

**Phase 5 - Final CGIP**

After a CGIP is voted upon, it will become a Final CGIP. Accepted Final CGIPs will move onto Phase 6, while rejected Final CGIPs will be available for resubmission following the resubmission guidelines, ending their lifecycle. This will be done by updating the proposal’s draft/metadata by a CGIP Editor, and should be completed within 72 hours. Proposals that fail to meet voting quorum (10% + 1 of circulating supply, as further detailed in CGIP-2) will be considered rejected. 

Duration of Phase 5 - 72 hours.

**Phase 6 - Implementation** 

Accepted Final CGIPs will move into Phase 6. Depending on the proposal, it will be up to various participants outlined below to ensure the success of the proposal, who will be outlined in the proposal itself. Rejected Final CGIPs will never enter Phase 6. 

Minimum duration of Phase 6 - N/A

### 4.4.1 Resubmission guidelines

Proposals that were rejected for any reason can be submitted up to 2 times. They must wait a minimum of 2 weeks, and make a substantial effort to solicit feedback as to why it was not originally approved, and implement the feedback as changes to the proposal. After the 3rd attempt to resubmit a given idea or CGIP, it will be permanently rejected and no longer able to be resubmitted for a subsequent vote. 

## 4.5. Details about The Creator’s Galaxy DAO

The Creator’s Galaxy DAO will give the community the ability to steward the future of The Creator’s Galaxy protocol, through voting on CGIPs via holding the $CLXY token. The Creator’s Galaxy protocol is dedicated to a permissionless and community owned ecosystem. By establishing a DAO and giving individual community members the ability to iterate, vote on, and execute decisions, we can truly empower the creators to own their own economy and community. 

### 4.5.1. DAO Voting requirements 

The votes shall adhere to the voting specifications within CGIP-2: Community Governance & Voting Model, which has been posted simultaneously with this CGIP-1 at [CGIP-2 link](https://discussions.creatorsgalaxyfoundation.com/t/cgip-2-community-governance-voting-model/19), and needs to achieve a quorum of at least 10% + 1 weight, of circulating $CLXY supply, for a vote to pass.

### 4.5.2. DAO Stewards 

The community will nominate a council of at least 6 Stewards (the “**Stewards Council**”), who will collectively manage the keys associated with the treasury’s multisig in accordance with the wishes of The Creator’s Galaxy DAO. Votes and changes to the token allocations, distributions, protocol standards, etc. can be proposed by anyone, as outlined above, and will result in a community vote in accordance to the governance process laid out in this CGIP-1. The 6 (or more) Stewards will endeavor to ensure that CGIPs are legally permissible, technically possible, and other criteria as laid out in Phase 3 of the CGIP process. For the avoidance of doubt, the Stewards Council is merely an administrator of The Creator’s Galaxy DAO’s decisions – it is not intended to exercise broad discretion, nor be tasked with responsibilities or expectations beyond ensuring that CGIPs have the required qualities as detailed in Phase 3 of the CGIP process and accordingly implementing such CGIPs pursuant to the vote of The Creator’s Galaxy DAO. It will ultimately be up to the community to drive the growth and development of The Creator’s Galaxy protocol and ecosystem.

The initial members of the Stewards Council are:

* **Andy Kulikyan**: Andy Kulikyan, Founder and CEO of Citadel Wallet, has 7+ Years of experience in embedded systems development for highly critical, secure and reliable Industrial, Military and Avionic applications. He has managed and led a team of multidisciplinary engineers to build out systems from concept to production stage such as Video and Data processing systems, Head Up Displays and Cameras for Military Aircrafts such as T-45, F-16, F-18, etc. He also has experience with supply chain management, addressing component lifetime/obsolescence issues and handling vendor/customer relationships. Simultaneously, he has been highly involved in the emerging Web 3 and Crypto space with a primary focus on next generation DLT platform Hedera and the vibrant ecosystem surrounding it.
* **Ashton Addison**: Ashton Addison is the founder of Crypto Coin Show, one of the longest standing news networks & interview shows in Web3, since 2014. He has hosted over 1,300 interviews with blockchain protocols, founders, future unicorn startups, and Web3 industry leaders. The Crypto Coin Show recently won the “Best Interview Show” in the industry at the 2022 Web3IAwards. He is also a public speaker with keynote speeches across Asia and North America. He’s also an active advisor to several blockchain companies across different networks.
* **Max Walker-Williams**: Max Walker-Williams is the founder and owner of the Walker&Williams Group, a diverse collection of businesses from property and 5* Hotels to Child care and Technology. Max shares what he learns and his day to day life in an honest and easy to understand way on his social media channels and successful YouTube channel.
* **Rahul Kothari**: Rahul is an engineer on Reddit’s Crypto team working on scalability and solving blockchain challenges. He previously worked at the Ethereum Foundation and was a core contributor at BlueSky - Jack Dorsey’s non profit to build decentralised social media. Rahul joined the Hedera space even before the testnet launch back in 2017 and performed a lot of work on Hedera’s smart contract service. He is also a technical advisor at Calaxy, Inc. and has co-authored a HIP.
* **Rufus Daniel**: Rufus brings three years of experience in Web3, including time as a Technical Writer, and is currently Social Media Manager for The HBAR Foundation. He has been an active member of the Hedera ecosystem throughout this time period and brings a passion for The Creator’s Galaxy and its mission to pioneer the Web3 creator economy.
* **Nick Crypto Crusader**: Nick, also known as NCashOfficial, is a content creator, investor, business owner and serial entrepreneur. He has amassed a large following across his social platforms, creating daily cryptocurrency content. He has created over 2,000 videos helping individuals see the value behind blockchain & distributed ledger technology. Outside of crypto, he owns & operates multiple online businesses, including a successful design agency.

At a minimum of every 12 months, there will be a DAO-wide vote to elect members of the Stewards Council. A member of the Stewards Council may be removed and replaced prior to their 12-month term pursuant to the voting requirements outlined in CGIP-2. Furthermore, pursuant to the voting requirements outlined in CGIP-2, the number of members of the Stewards Council can be increased and members elected to fill such additional seats.

## 4.6. Parts of a CGIP & Key Terms

***Each CGIP is required to have the following parts/sections:***

1. Preamble -- RFC 822 style headers containing meta-data about the CGIP, including the CGIP number, a short descriptive title (limited to a maximum of 44 characters), the names and, optionally, the contact info for each author, etc.

Each CGIP must begin with a header preamble in list format. The headers must appear in the following order. 

* cgip: CGIP number
* title: CGIP title
* author: a list of the author’s or authors’ name(s) and/or username(s), or name(s) and email(s).
* type: <Standards Track | Grants | Informational | Process>
* \* category: <Core | Governance | Economics >
* status: < >
* created: date created on
* \* discussions-to: a URL pointing to the official discussion thread
* \* updated: comma separated list of dates
* \* requires: CGIP number(s)
* \* replaces: CGP number(s)
* \* superseded-by: CGIP number(s)

Headers marked with “*” are optional and are described below. All other headers are required.

### `author` header

The author header lists the names, email addresses or GitHub usernames of the authors/owners of the CGIP. Those who prefer anonymity may use a username only, or a first name and a username. The format of the author header value must be:

Random J. User <address@dom.ain>

or

Random J. User (@username)

if the email address or GitHub username is included, and Random J. User

if email or username are not given.

At least one author must use a GitHub username in order to be notified on change requests and have the capability to approve or reject them.

### `discussions-to` header

While a CGIP is a draft, a discussions-to header will indicate the URL where the CGIP is being discussed.

No discussions-to header is necessary if the CGIP is being discussed privately with the author.

As a single exception, discussions-to cannot point to GitHub pull requests.

### `type` header

The Type header specifies the type of CGIP: Standards Track, Grants, Informational, or Process. If the track is Standards, the CGIP must include the category header.

### `category` header

The category header specifies the CGIP category (Core, Economics, Governance). This is required for Standard Track CGIPs only.

### `created` header

The created header records the date that the CGIP was assigned a number. This header should be in ISO 8601 format (yyyy-mm-dd), e.g. 2019-09-16.

### `updated` header

The updated header records the date(s) when the CGIP was updated with “substantial” changes. The header is only valid for CGIPs of Draft and Active status. This header should be in ISO 8601 format (yyyy-mm-dd), e.g. 2019-09-16.

### `requires` header

CGIPs may have a requires header, indicating the CGIP numbers that this CGIP depends on.

### `superseded-by` and `replaces` headers

CGIPs may also have a superseded-by header indicating that a CGIP has been rendered obsolete by a later document; the value is the number of the CGIP that replaces the current document. The current document must change status to “Replaced” once the superseding CGIP is changed to “Final” status. The newer CGIP must have a replaces header containing the number of the CGIP that it rendered obsolete.

2. Abstract -- a short (~200 words or fewer) description of the issue being addressed.

3. Motivation -- The motivation should clearly explain why the existing specification is inadequate to address the problem that the CGIP solves. 

4. Rationale -- The rationale fleshes out the specification by describing why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages.

5. User stories -- Provide a list of "user stories" to express how this feature, functionality, improvement, or tool will be used by the end user - whether that be fans or creators within the ecosystem. This field is optional, depending on the type of proposal.

6. Specification -- The technical specification should describe the syntax and semantics of any new features. The specification should be detailed enough to allow competing, interoperable implementations (for at least the current Hedera ecosystem, but ideally, all web3 ecosystems).

7. Steps to Implement – The steps to implement the proposal, including associated costs, and technical, administrative, legal or other required actions. This section should also include any already-taken steps.

8. References -- A collection of URLs used as references through the CGIP. 

References to other CGIPs should follow the format CGIP-N where N is the CGIP number you are referring to. Each CGIP that is referenced in an CGIP MUST be accompanied by a relative markdown link the first time it is referenced, and MAY be accompanied by a link on subsequent references.

Images, diagrams, and auxiliary files should be included in a subdirectory of the assets folder for that CGIP as follows: assets/cgip-N (where N is to be replaced with the CGIP number). When linking to an image in the CGIP, use relative links such as ../assets/cgip-1/image.png.

9. Copyright/license -- Each new CGIP must be placed under the MIT License [MIT License (mit-license.org)](https://mit-license.org/).

***Each CGIP can optionally have the following items. Including these sections may increase the likelihood of a proposal’s success - ***

10. Backwards Compatibility -- All CGIPs that introduce backward incompatibilities must include a section describing these incompatibilities and their severity.  This field is optional, depending on the type of proposal.

11. Security Implications -- If there are security concerns in relation to the CGIP, those concerns should be explicitly addressed to make sure reviewers of the CGIP are aware of them. This field is optional, depending on the type of proposal.

12. How to Teach This -- For a CGIP that adds new functionality or changes interface behaviors, it is helpful to include a section on how to teach users, new and experienced, about the new feature.  This field is optional, depending on the type of proposal.

13. Reference Implementation -- The reference implementation must be complete before any CGIP is given the status of “Final”. The final implementation must include test code and documentation.  This field is optional, depending on the type of proposal.

14. Rejected Ideas -- Throughout the discussion of a CGIP, various ideas will be proposed which are not accepted. Those rejected ideas should be recorded along with the reasoning as to why they were rejected. This both helps record the thought process behind the final version of the CGIP as well as preventing people from bringing up the same rejected idea again in subsequent discussions.  This field is optional, depending on the type of proposal.

    In a way, this section can be thought of as a breakout section of the Rationale section that focuses specifically on why certain ideas were not ultimately pursued.

15. Open Issues -- While a CGIP is in draft, ideas can come up which warrant further discussion. Those ideas should be recorded so people know that they are being thought about but do not have a concrete resolution. This helps make sure all issues required for the CGIP to be ready for consideration are complete and reduces people duplicating prior discussions.  This field is optional, depending on the type of proposal.

## 4.7. CGIP Formats and Templates

CGIPs should be written in markdown format. An example template will be released by The Creator’s Galaxy Foundation shortly after the posting of this CGIP-1. 


# 5.	Steps to Implement

    a.  Approve the CGIP process as proposed in this CGIP-1

    b.  Ratify the formation of The Creator’s Galaxy Foundation

    c.  Approve The Creator’s Galaxy Foundation’s governing documents (Amended & Restated Memorandum and Articles of Association + Charter, the forms of each which are attached hereto)

    d.  Approve the appointment of each of the Stewards to the Stewards Council

    e.  Propose a voting process and implement such process (see CGIP-2 at [CGIP-2 link](https://discussions.creatorsgalaxyfoundation.com/t/cgip-2-community-governance-voting-model/19))

    f.  Completed setup of the Discourse settings

    g.	Approve reimbursements + ongoing costs

        i.	Initial Setup Costs of The Creator’s Galaxy Foundation and The Creator’s Galaxy DAO

            1.	Setup Costs including domain purchases and fees, legal fees, DAO administration setup, Discourse Enterprise and setup, and misc out of pocket costs. $100,000

        ii.	Ongoing costs
        
            1.	Supervisor, secretary and director fees: $35K USD per annum, contracted for an indefinite term

            2.	Discourse Enterprise Account: Discussion platform to host all topics discussed by the community before formalizing into proposals. $300 per month, on month-to-month basis

        iii.	Stewards Council Compensation

            1.	Compensation is in the form of $CLXY to align incentives of members of the Stewards Council with The Creator’s Galaxy DAO.

            2.	Each Council member receives $100,000 in $CLXY for their 12-month term, subject to equal monthly vesting over the course of their term (~$8,333.33 of $CLXY/month for 12 months).

    h.	Approve the below token allocations in accordance with [The Creator’s Galaxy whitepaper](https://www.creatorsgalaxyfoundation.com/whitepaper.pdf). Upon approval of this CGIP-1, each of the allocations below marked with an asterisk * will be sent to a multi-signature wallet with each of the Stewards as signatories.

	    i.      46M to Investors
        ii.     55M to Community Grants*
        iii.    100M for Creator Grants*
        iv.     100M for Ecosystem Grants*
        v.      150M to Team
        vi.     200M to Calaxy, Inc. 
        vii.    349M for General Treasury Use*

# 6. References

* [The Creator’s Galaxy Whitepaper](https://www.creatorsgalaxyfoundation.com/whitepaper.pdf)
* [Hedera Hashgraph’s Documentation](https://docs.hedera.com/hedera/)

# 7. Copyright

This document is licensed under the MIT License [MIT License (mit-license.org)](https://mit-license.org/)