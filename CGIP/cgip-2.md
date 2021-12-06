- cgip: 2
- title: Creator Application Whitelists
- author: @paulatcalaxy
- type: Standards Track 
- category: Core 
- status: < >
- created: November 5/2021
- discussions-to: 
- updated: 
- requires: na
- replaces: na
- superseded-by: 

## Abstract

Creators Application Whitelists allow a Creator to define a list of 3rd party applications that are 'approved' by that Creator - and so signalling to Fans the authenticity of applications on the list.

## Motivation

When visting a 3rd party application that claims to be selling an asset or service from a particular Creator, Fans must be able to verify the authenticity of that application, and so the asset or service.

One mechanism for giving Fans this confidence is to allow each Creator to manage and publish an application whitelist of approved applications. Once an application was added to a Creator's whitelist (presuming some offline business deal), Fans considering buying some asset from the corresponding Creator via that application would be able to 'query' the whitelist to determine if the application was approved.

Importantly, it must be possible for an application to be removed from a Creator's whitelist when appropriate - as determined by the Creator.

Each Creator will have their own Application Whitelist with potentially a unique list of approved applications - though there is likely to be much overlap.

## Rationale
When building permissionless applications on blockchains, or distributed ledgers like Hedera, anyone can implement the tokens living on that ledger. Projects such as Bitclout have gone ahead and minted social tokens on behalf of celebrities without their consent. Within The Creator's Galaxy, there is a ambition to be as veriable and opt-in as possible, particularly when it comes to endorsing platforms that an individuals "fans" may wish to use. By defining an approved list of applications that a Creator has "verified" they wish their social tokens to be used within, it can bolster additional value to the the social token as a viable form of payment with customizable rewards/incenties, help transparently identify where fans can utilize those tokens, and additionally reduce potential fraud/scams of platforms non-consensually integrating a Creator's social token. 

## User Stories

Creators

1. A Creator (or their delegate) will login to their admin page
2. The Creator will navigate to a 'Manage Approved Applications' screen
3. The Creator will be able to view the current list of approved applications, add to the list, or remove an application from the list
4. When adding an application, the Creator will stipulate the name and address of the new application

Fans

1. A Fan will be provided with the ability to view a Creators list of approved applications
2. A fan will have the ability to determine if a particular application is approved

## Specification

A Creator's 'application whitelist' will manifest as a JSON file on Hedera's file service. It is by creating and updating this file that a Creator will manage their application whitelist. If an application is listed in a Creator's whitelist, then Fans can interpret that to mean that the application is approved to sell assets or services of the Creator.

It is by viewing the contents of this file (or otherwise be presented with some UI indicator of an application being there listed) that Fans will be able to determine the authenticity of applications.

### Application Whitelist Schema 

The application whitelist is a JSON file listing the applications that have been approved by the Creator.

Each entry in the list stores a name, TLD URL, and approval date for a particular application


    [
	    {
		    name: "Shopify",
		    URL: "www.shopify.com",
		    date: "14-11-2021" 
	    },
	    {
		    name: "AppB",
		    URL: "www.appb.com",
		    date: "16-12-2021"
	    },
    ]

The order of entries in the list is not material.

### Binding Whitelist to Creator

It must be possible to establish that a given application whitelist (with a given Hedera File identifier) is associated with a particular Creator (as identified by their social token's token identifier). If not, a malicious application could direct a Fan to a fake application whitelist with its own name on the list - fooling the Fan into thinking the application was valid and approved by the Creator when in fact it wasn't.

The Creator's social token's memo field will be used to point to the appropriate application whitelist. 

Rather than directly specifying the file identifier within the memo field, the memo field will contain a Decentralized Identifier (DID) that itself 'points' to a JSON DID Document stored off chain (in an HCS appnet run by participants in the Creator's Galaxy). The DID Document will contain the File identifier of the application whitelist.

The sequence by which an application whitelist is resolved is as follows

```
Query Token -> 
     Determine DID from memo field -> 
           Resolve DID into DID Document -> 
	         Determine application whitelist file identifier -> 
		        Retrieve application whitelist JSON
```

While the DID model introduces an extra lookup, it provides a flexible integration point for the future. 

As an example, we can in the future leverage the DID mechanism to bind a Verifiable Credential issued to the Creator to the social token in the same manner as for this application whitelist. 

Additinally, the DID model allows for the location of the application whitelist to be changed to other than Hedera's file service, eg IPFS, without editing the token itself.

### DID Document Schema

A DID document contains a set of service endpoints. 

We will extend the schema with a service endpoint of type 'CalaxyApplicationWhitelist'

    {
      "service": [{
        "id":"did:hedera:mainnet:123sjgjhdfughdiufg#application-whitelist",
        "type": "CalaxyApplicationWhitelist", 
        "serviceEndpoint": "0.0.12345"
      }]
    }

The serviceEndpoint carries the Hedera File identifier of the application whitelist.

## Backwards Compatibility

N/A

## Security Considerations

N/A

## How To Teach This

There exists a public list on the Hedera network. That list includes applications a Creator has verified for usage of their social tokens. There may be additional applications utilizing their social tokens beyond those defined in this list, but those included are "verified" in the practical sense. 

## Reference Implementation

View the Application Schema above..

## Rejected Ideas

Nothing has been rejected yet!

## Open Issues

Could we imagine building this using Verifiable Credentials issued by the Creator to each approved application attesting to that approval?

How does an application prove it is on a Creator's application whitelist other than giving a Fan the ability to view the whitelist and manually compare the entries to the application's own TLD? Might the application whitelist contain DIDs, and the applications would demonstrate ownerhip of their own DID?

## References 

[Bitclout](https://bitclout.com)

## Copyright

N/A

