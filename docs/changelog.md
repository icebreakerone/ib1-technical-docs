
# Changelog

## Version 0.3beta, 6 September 2024

* Rename Group to Roles.
* Change values of `ib1:sensitivityClass` to URLs, retaining the class names.
* Change values of `ib1:datasetAssurance` to URLs, with values using correct naming conventions.
* Change URLs for Grants and Obligations to use correct naming conventions.
* `dcterms:license` is the URL of a Licence Interpretation.
* Add ib1:publisherRole to Scheme Catalog Requirements

## Version 0.2beta, 22 June 2024

* [Catalog Metadata](metadata.md) is now a DCAT Dataset or Data Service, extended with IB1 terms.
	* Standard terms now have restricted meanings when used with a Trust Framework.
	* Format of data and API responses are specified in external files in the Registry for standardisation.
	* Both Dataset and Data Service DCAT types are used.
* [Access control](access_control_specification.md) updated to
	* remove complex, reducing to a simple statement that one or more groups can access a dataset under a single licence.
	* added machine readable interpretation of licences.
	* renamed "Permissions" to "Grants" to clarify intent and avoid a name clash with another concept.
* [Scheme Catalog Requirements](scheme_catalog_requirements.md) are added to define how data sources comply with standards across the Scheme.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NDA0NDk1ODEsMzY1Mzc5Mjc5LDE3OD
k1OTg1MTcsLTE4NjAwNzUwODBdfQ==
-->