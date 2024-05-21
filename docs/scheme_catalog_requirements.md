
# Scheme Catalog Requirements

A Scheme Catalog Requirements Document specifies the metadata that a DCAT Catalog entry must contain for it to be Scheme-conforming, representing a data source that meets a common standard across a Scheme to provide the same format and meaning of data across all Data Providers.

It is an RDF document published by the Registry.

## Example

```
@prefix ib1: <http://registry.ib1.org/ns/1.0/>

<https://registry.ib1.org/scheme/catalog-requirements/energy-report>
	a ib1:SchemeCatalogRequirements ;
	dcterms:title "Energy Report Requirements" ;
	ib1:requiredType dcat:DataService ;
	ib1:requiredMetadata [ a ib1:RequiredMetadata ;
	];
	ib1:
.
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMTczMDE1ODgsMTI2ODgzNjcwOF19
-->