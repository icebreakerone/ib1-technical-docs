
# Scheme Catalog Requirements

A Scheme-conforming data source meets a common standard across a Scheme. These standards are followed by the Data Providers so that the same kind of data is published across the Scheme using the same APIs, formats and meaning of data. A Scheme Catalog Requirements Document specifies the metadata that a DCAT Catalog entry must contain for it to be Scheme-conforming, and which roles may publish a conforming data source. 

It is an RDF document published in the Registry, and the metadata links to machine readable Licence, API and format specifications which are also published in the Registry.

## Example

```
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix dcat: <http://www.w3.org/ns/dcat#> . 
@prefix ib1: <https://registry.core.trust.ib1.org/ns/1.0#> .

<https://registry.core.trust.ib1.org/scheme/electricity/standard/supply-voltage>
		a ib1:SchemeCatalogRequirements ;
	dcterms:title "Supply Voltage API Requirements" ;
	ib1:requiredType dcat:DataService ;
	ib1:roleRequiredToPublish <https://registry.core.trust.ib1.org/scheme/electricity/role/generator> ;
	ib1:requiredMetadata [ a ib1:RequiredMetadata ;
	    dcat:endpointDescription <https://registry.core.trust.ib1.org/scheme/electricity/api/voltage> ;
	    ib1:heartbeatDescription <https://registry.core.trust.ib1.org/api/heartbeat-simple/1.0> ;
	    ib1:sensitivityClass ib1:IB1-SA ;
	    ib1:roleRequiredToAccess <https://registry.core.trust.ib1.org/scheme/electricity/role/network-operator> ;
	    ib1:roleRequiredToAccess <https://registry.core.trust.ib1.org/scheme/electricity/role/report-provider> ;
	    dcterms:licence <https://registry.core.trust.ib1.org/scheme/electricity/licence/voltage-reporting/1.4> ;
	];
	ib1:requireAllAndAllowAdditional ib1:roleRequiredToAccess ;
	ib1:requireAbsenceOf ib1:oauthIssuer ;
.
```

This example defines a standard Supply Voltage API that is provided by multiple providers in a Trust Framework. It specifies the API in detail with the `dcat:endpointDescription` referring to an OpenAPI specification hosted by the Registry. It uses a standard `ib1:heartbeatDescription` to check for liveness, using a standard heartbeat request defined in an OpenAPI specification hosted by the Registry.

For access control, it specifies the `ib1:sensitivityClass`, and who can use the API with `ib1:roleRequiredToAccess`. Because `ib1:requireAllAndAllowAdditional` is used for the access rules, it allows the publisher to widen access to additional roles, as long as the roles in this document are included.

Because the API does not require end user consent, `ib1:requireAbsenceOf` is used to prohibit the use of an OAuth Issuer.

## Versions

The URL of a Scheme Catalog Requirements Document is a stable identifier that is used to find data sources in the Catalog by searching for all entries with this URL in the `dcterms:conformsTo` term.

Scheme Catalog Requirements Documents are not versioned, and do not include version numbers in their URLs. Versioned URLs would prevent easy searching with SPARQL queries, and require a range of compatible versions to be included in the record.

Scheme Catalog Requirements Documents may be updated with backwards compatible changes, for example, adding additional roles who are permitted to use the data source. Existing records are not updated automatically. A compliance process will detect out-of-date catalog entries, and notify providers to review the changes and update their record.

## Object specification

An `ib1:SchemeCatalogRequirements` RDF object must contain these fields:

`ib1:requiredType`
: The type of the DCAT Catalog entry which describes this data source.

`ib1:requiredMetadata`
: A bnode which contains the metadata required to be Scheme-conforming. This bnode may contain any fields and metadata, and a conforming catalogue entry must contain it all, subject to the term modifiers.

`ib1:roleRequiredToPublish`
: The URL of the Role which is permitted to publish a Catalog entry conforming to this standard. If multiple Roles are specified, any of those Roles may publish a catalog entry.

### Term modifiers

The requirements for terms in the `ib1:requiredMetadata` are modified by terms in the top level object.

(no modifier)
: All the values in the requirements must be included for a term which does not have a modifier. No additonal values for that term are allowed.

`ib1:requireAllAndAllowAdditional <term>`
: All the values in the requirements must be included for this term, but additional values are allowed.

`ib1:requireAnyOneOf <term>`
: Exactly one of the values in the requirements must be included for this term. No other values are allowed.

`ib1:requireAnyValue <term>`
: The term must be present, with any valid value.

`ib1:requireAbsenceOf <term>`
: The term must not be present.

