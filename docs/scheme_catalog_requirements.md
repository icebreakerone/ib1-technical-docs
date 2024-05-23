
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
	    ib1:permitGroup <https://directory.ib1.org/group/network-operator> ;
	    ib1:permitGroup <https://directory.ib1.org/group/report-provider> ;
	    dcterms:licence <https://creativecommons.org/licenses/by/4.0/> ;
	];
	ib1:include-all-allow-additional ib1:permitGroup ;
.
```

This example defines a standard Supply Voltage API that is provided by multiple providers in a Trust Framework. It specifies the API in detail with the `dcat:endpointDescription` referring to an OpenAPI specification hosted by the Registry. It uses a standard `ib1:heartbeatDescription` to check for liveness, using a standard heartbeat request defined in an OpenAPI specification hosted by the Registry.

For access control, it specifices the `ib1:sensitivityClass`, and who can use the API with `ib1:permitGroup`. Because `ib1:include-all-allow-additional` is used for the access rules, it allows the publisher to widen access to additional groups and roles, as long as the groups in this document are included.

## Object specification

An `ib1:SchemeCatalogRequirements` RDF object must contain these fields:

`ib1:requiredType`
: The type of the DCAT Catalog entry which describes this data source.

`ib1:requiredMetadata`
: A bnode which contains the metadata required to be Scheme-conforming. This bnode may contain any fields and metadata, and a conforming catalogue entry must contain it all, subject to the term modifiers.

### Term modifiers

The requirements for terms in the `ib1:requiredMetadata` are modified by terms in the top level object.

(no modifier)
: All the values in the requirements must be included for a term which does not have a modifier. No additonal values for that term are allowed.

`ib1:include-all-allow-additional <term>`
: All the values in the requirements must be included for this term, but additional values are allowed.

`ib1:include-one-of <term>`
: Exactly one of the values in the requirements must be included for this term. No other values are allowed.


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTExMzEyODk2OSwxMjY4ODM2NzA4XX0=
-->