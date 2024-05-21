
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
	    dcterms:conformsTo <https://registry.ib1.org/class/supply-voltage> ; 
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

This example defines a standard Supply Voltage API that is provided by 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkwNDMzMzQyNiwxMjY4ODM2NzA4XX0=
-->