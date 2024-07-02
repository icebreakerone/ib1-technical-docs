
# Scheme Catalog Requirements

A Scheme Catalog Requirements Document specifies the metadata that a DCAT Catalog entry must contain for it to be Scheme-conforming. A conforming data source meets a common standard across a Scheme, where all Data Providers provide the same APIs, formats and meaning of data.

It is an RDF document published by the Registry.

## Example

```
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix dcat: <http://www.w3.org/ns/dcat#> . 
@prefix ib1: <http://registry.ib1.org/ns/1.0#> .

<https://registry.estf.ib1.org/scheme/electricity/standard/supply-voltage>
		a ib1:SchemeCatalogRequirements ;
	dcterms:title "Supply Voltage API Requirements" ;
	ib1:requiredType dcat:DataService ;
	ib1:requiredMetadata [ a ib1:RequiredMetadata ;
	    dcat:endpointDescription <https://registry.estf.ib1.org/scheme/electricity/api/voltage> ;
	    ib1:heartbeatDescription <https://registry.estf.ib1.org/api/heartbeat-simple/1.0> ;
	    ib1:sensitivityClass "IB1-SA" ;
	    ib1:permitGroup <https://directory.estf.ib1.org/scheme/electricity/group/network-operator> ;
	    ib1:permitGroup <https://directory.estf.ib1.org/scheme/electricity/group/report-provider> ;
	    dcterms:licence <https://registry.estf.ib1.org/scheme/electricity/licence/voltage-reporting/1.4> ;
	];
	ib1:includeAllAllowAdditional ib1:permitGroup ;
.
```

This example defines a standard Supply Voltage API that is provided by multiple providers in a Trust Framework. It specifies the API in detail with the `dcat:endpointDescription` referring to an OpenAPI specification hosted by the Registry. It uses a standard `ib1:heartbeatDescription` to check for liveness, using a standard heartbeat request defined in an OpenAPI specification hosted by the Registry.

For access control, it specifies the `ib1:sensitivityClass`, and who can use the API with `ib1:permitGroup`. Because `ib1:includeAllAllowAditional` is used for the access rules, it allows the publisher to widen access to additional groups, as long as the groups in this document are included.

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

`ib1:includeAllAllowAdditional <term>`
: All the values in the requirements must be included for this term, but additional values are allowed.

`ib1:includeOneOf <term>`
: Exactly one of the values in the requirements must be included for this term. No other values are allowed.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NzMwMjMzNTEsOTk1NjgzMTc5LDE0ND
Q4NzU4MjUsNjc0NTc2NDgxLC0xNzk0NDk1MDQ2LC01Mjg2NDU3
MzcsMTM4OTcwMjAzOCwxMTEzMTI4OTY5LDEyNjg4MzY3MDhdfQ
==
-->