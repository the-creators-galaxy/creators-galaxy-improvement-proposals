- cgip: 3
- title: Creator Verifiable Credential Schema
- author: @paulatcalaxy
- type: Standards Track 
- category: Core 
- status: < >
- created: November 15/2021
- discussions-to: 
- updated: 
- requires: na
- replaces: na
- superseded-by: 

## Abstract

A Creator Verifible Credential asserts the identity attributes like social media accounts, corresponding number of followers, sports team they play for, achievement & awards etc that collectively establish their credenibility as a Creator. The Creator Verifiable Credential Schema stipulates the attributes , both required and optional, that are found in  such a Verifiable Credential for Creators participating in the Creator's Galaxy. 

## Motivation

The Creator's Galaxy connects Creators and Fans in new economic models. For a Fan to be willing to pay for an engagement (such as a video call, or social follow etc)  or interaction with a Creator, they must be confident that the Creator is authentic. A Verifiable Credential for a Creator is a secure and trustworthy attestation to that authenticity. A Creator's VC lists the identity attributes for that Creator - attributes such as name, accounts on other social networks, and affiliations.  It is by verifying a VC that a Fan can be confident that they are indeed interacting with an authentic Creator, and so be willing to pay for that engagement.

## Rationale


## User Stories

Creators

1. A Creator authenticates to an Identity Provider within the Creator's Galaxy
2. The Creator verifies their identity with the IdP
3. The Creator is issued a Verifiable Credential attesting to relevant attributes of their identity.



## Specification

The Creator Verifiable Credential Schema uses JSON Schema to specify the required and optional identity attributes to be found within VCs issued to Creators.

### Creator Verifiable Credential Attributes

1. First Name - Required
2. Last Name - Optional
3. socialURL - Required

### Creator Verifiable Credential Schema 

Below is the JSON Schema 

```
    {
	"type": "https://w3c-ccg.github.io/vc-json-schemas/schema/2.0/schema.json",
	"version": "1.0",
	"id": "did:hedera:AsFhHzhwUvGNuYkX7T",
	"name": "Creator Credential",
	"author": "did:hedera:MDP8AsFhHzhwUvGNuYkX7T",
	"authored": "2021-01-01T00:00:00+00:00",
	"schema": {
		"$id": "creator-schema-1.0",
		"$schema": "https://json-schema.org/draft/2020-12/schema",
		"description": "A schema template for Creator Verifiable Credentials",
		"type": "object",
		"properties": {
			"firstName": {
				"type": "string",
				"format": "name"
			},
			"secondName": {
				"type": "string",
				"format": "name"
			},
			"socialURL": {
				"type": "string"
			}
		},
		"required": ["firstName", "socialURL"],
		"additionalProperties": false
	}
    }
```


## Backwards Compatibility

N/A

## Security Considerations

N/A

## How To Teach This

A Creator's Verifiable Credential attests to the aspects of their identity relevant to participants in the Creator's Galaxy. Participants in the ecosystem will expect there to be consistency in what attributes are in these credentials. This specification stipulates which attributes must be found in a VC, and which others may be found.

## Reference Implementation

## Rejected Ideas

Nothing has been rejected yet!

## Open Issues

## References 

## Copyright

N/A
