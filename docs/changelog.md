
# Changelog

## Version 0.4beta, 03 July 2025

* Move technical specifications to [specification.docs.ib1.org](https://specification.docs.ib1.org)
* Remove redundant materials.
* Change Registry URLs and IB1 terms to use new style hostnames under `trust.ib1.org`.

## Version 0.3beta, 10 September 2024

* Rename Group to Roles, with `ib1:permitGroup` renamed to `ib1:roleRequiredToAccess`
* Change values of `ib1:sensitivityClass` to URLs, retaining the class names.
* Change values of `ib1:datasetAssurance` to URLs, with values using correct naming conventions.
* Change URLs for Grants and Obligations to use correct naming conventions.
* `dcterms:license` is the URL of a Licence Interpretation.
* Add `ib1:roleRequiredToPublish` to Scheme Catalog Requirements

## Version 0.2beta, 22 June 2024

* Catalog Metadata is now a DCAT Dataset or Data Service, extended with IB1 terms.
	* Standard terms now have restricted meanings when used with a Trust Framework.
	* Format of data and API responses are specified in external files in the Registry for standardisation.
	* Both Dataset and Data Service DCAT types are used.
* Access control updated to
	* remove complex, reducing to a simple statement that one or more groups can access a dataset under a single licence.
	* added machine readable interpretation of licences.
	* renamed "Permissions" to "Grants" to clarify intent and avoid a name clash with another concept.
* Scheme Catalog Requirements are added to define how data sources comply with standards across the Scheme.

