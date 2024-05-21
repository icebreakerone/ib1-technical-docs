
# Scheme Catalog Requirements

A Scheme Catalog Requirements Document specifies the metadata that a DCAT Catalog entry must contain for it to be Scheme-conforming, representing a data source that meets a common standard across a Scheme to provide the same format and meaning of data across all Data Providers.

It is an RDF document published by the Registry.

## Example

```
@prefix ib1: <http://registry.ib1.org/ns/1.0/>

<https://registry.ib1.org/class/supply-voltage>
	a ib1:SchemeCatalogRequirements ;
	dcterms:title "Supply Voltage API Requirements" ;
	ib1:requiredType dcat:DataService ;
	ib1:requiredMetadata [ a ib1:RequiredMetadata ;
	    dcat:endpointDescription <https://registry.ib1.org/api/electricty-voltage> ;
	    ib1:heartbeatDescription <https://registry.ib1.org/api/heartbeat-simple> ;
	    ib1:sensitivityClass "IB1OE-SA" ;
	    ib1:access [ a ib1:AccessRule ;
	        ib1:group <https://directory.ib1.org/group/report-provider> ;
	        ib1:licence <https://creativecommons.org/licenses/by/4.0/> ;
	    ];
	];
	ib1:match-at-least ib1:access ;
.
```

This example defines a standard Supply Voltage API that is provided by multiple providers in a Trust Framework. It specifies the API in detail with the `dcat:endpointDescription` referring to an OpenAPI specification hosted by the Registry. It uses a standard `ib1:heartbeatDescription` to check for liveness, using a standard heartbeat request defined in an OpenAPI specification hosted by the Registry.

For access control, it specifices the `ib1:sensitivityClass`, and who can use the API with `ib1:access`. Because `ib1:match-at-least` is used for the access rules, it allows the publisher to widen access with additional access rules, as long as the rules in this document are included.

## Object specification

An `ib1:SchemeCatalogRequirements` RDF object must contain these fields:

`ib1:requiredType`
: The type of the DCAT Catalog entry which describes this data source.

`ib1:requiredMetadata`
: A bnode which contains the metadata required to be Scheme-conforming. This bnode may contain any fields and metadata, and a conforming catalogue entry must contain it all, subject to the term modifiers.

### Term modifiers

Terms in the `ib1:requiredMetadata`


<!--stackedit_data:
eyJoaXN0b3J5IjpbODAzOTAwOTQ1LDEyNjg4MzY3MDhdfQ==
-->