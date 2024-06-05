# Dataset & Data Service Metadata

Each [Data Provider](glossary.md#term-Data-Provider) maintains a set of one or more metadata files, each of which can describe one or more 
distinct sources of data. These descriptions serve several purposes:


1. They drive discovery descriptions are ingested into our search system and made available to a [Data Consumer](glossary.md#term-Data-Consumer) 
searching for particular kinds of data.


2. They inform consumption of that data, providing information on:


    1. The [API](glossary.md#term-Application-programming-interface) required to access the data source


    2. Any access constraints which may need to be satisfied


    3. Licenses for any accessed data


    4. Representation and internal semantics of expressions of the data

## Dataset or Data Service?

A Dataset:
* is provided as one or more downloadable files,
* may be published as part of series of Datasets covering the same source of data over different time periods, and
* should maintain historical access to previous periods.

A Data Service:
* is an API to query some data which uses parameters to specify a subset of data, including time period,
* is specified formally by a machine readable API description, and
* may require consent from a data subject external to the Trust Framework.

They are described by slightly different information in metadata files.

## Scheme-conforming

A Scheme-conforming Dataset or Data Service meets the data format and meaning requirements of the Scheme, along with any required access and licence conditions.

These requirements are published by the Scheme Registry as machine readable [Scheme Catalog Requirements Documents](scheme_catalog_requirements.md), and metadata files link to them to show their conformance.

Most Datasets and Data Services are Scheme-conforming. A Data Provider may publish data which is not Scheme-conforming to:
* use Scheme licences and roles to share ad-hoc Shared Data with Scheme participants (where the Scheme doesn't expressly disallow this), or
* use the Catalog to include Open Data in a public index.

## Metadata File Structure

The metadata is a standard [DCAT](https://www.w3.org/TR/vocab-dcat-3/) RDF file representing one or more sources of data. 

**NOTE**: The examples below use the [Turtle](https://www.w3.org/TR/turtle/) format for compactness and increased readability. Data providers may present this information in Turtle, RDF/XML, JSON-LD or N3 formats.

Datasets are represented as Dataset DCAT objects with one or more Distributions. If the data measures the same thing over periods of time, then these must be linked together with a Data Series object. The format of the data is described by JSON Schema, XSD 1.1 or CSVW schemas.

Data Services are represented as Data Service DCAT objects, with [OpenAPI](https://swagger.io/specification/) specifications of the API and the format of the data in the responses.

The URL of the DCAT object inside the RDF representation is the stable identifer of the Dataset or Data Service. This must remain constant each time the metadata file is fetched and over updates to the metadata.

## Mandatory metadata fields

The following fields must be included in every DCAT object. Metadata will be visible to all pariticipants in the Trust Framework, and may be visible to anyone on the open web without authentication in an open index.

[dcterms:title](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/title/)
: Short title for this dataset.

[dcterms:publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/)
: The URL of the Data Provider's record in the Scheme Directory.

[dcterms:license](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#license)
: The URL of a Licence. All use of this data source is subject to this Licence. Where a data source is Scheme-conforming, the URL will be registered in the Registry.

`ib1:trustFramework`
: The URL of the Trust Framework(s) the dataset is assured under.

`ib1:datasetAssurance`
: The assurance level for this dataset.

`ib1:sensitivityClass`
: The [data sensitivity class](glossary.md#term-Data-sensitivity-class) of this dataset. In the current IB1 Trust Framework this should always be one of [IB1-O](glossary.md#term-Data-sensitivity-class-open),  [IB1-SA](glossary.md#term-Data-sensitivity-class-shared-A) or [IB1-SB](glossary.md#term-Data-sensitivity-class-shared-B), no other classes are permitted. The value of this property also determines the level of [API](glossary.md#term-Application-programming-interface) security imposed, with [IB1-O](glossary.md#term-Data-sensitivity-class-open) datasets being open data with no additional security, and the two shared data classes mandating [FAPI](glossary.md#term-Financial-Grade-API) security using the IB1 Trust Framework.

Additional fields may be made mandatory for Scheme-confirming data sources by the Scheme Catalog Requirements Document.

## Conformance and access control metadata fields

`dcterms:conformsTo`
: The URL of a Scheme Catalog Requirements Document in the Scheme Registry. Most metadata files will include this field.

`ib1:permitGroup`
: The URLs of one or more groups in the Directory which may access this data source subject to the Licence in the `dcterms:license` term, unless the data is open data with a `ib1:sensitivityClass` of `IB1-O`. See [Access Control Specification](access_control_specification.md).

## Data Service metadata fields

Data Services are represented by `dcat:DataService` objects with the common mandatory fields and Data Service specific fields.

`dcat:endpointDescription`
: The URL of an OpenAPI file, which fully documents the request parameters and responses. Responses must use XML or JSON. To allow the OpenAPI file to be used by multiple Data Providers, the file may only contain a single [Server object](https://swagger.io/specification/#server-object), where the `url` is `"{endpointURL}"`, and `variables` sets the default to `"https://endpointurl-not-specified.ib1.org"`.

`dcat:endpointURL`
: The URL of this specific instance of the API. It is interpolated into the `url` specified in the OpenAPI file using the `endpointURL` variable.

`ib1:heartbeatDescription`
: An optional URL of an OpenAPI file (with Server specified as `dcat:endpointDescription`), which contains a single Path with a 200 response defined. This term will typically be the URL of one of a small number of standard OpenAPI files published in the Registry.

Any additional metadata defined by published Standards may be added.

## Dataset metadata fields

Datasets are represented by `dcat:Dataset` objects with the common mandatory fields and Dataset specific fields.

As Datasets will be discovered by browsing an index, they need additional descriptive metadata for discovery. The following fields are mandatory:

[dcterms:description](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/description/)
: Longer form description of this dataset. This is used in combination with the title and tags when people search for datasets, so aim to include probable search words in the description.

[dcat:distribution](https://www.w3.org/TR/vocab-dcat-3/#Property:dataset_distribution)
: URL of a `dcat:Distribution` for a downloadable file, see below for mandatory fields. Multiple Distributions may be defined for the same data in different formats, taking into account any requirements and restrictions for Scheme-conforming datasets.

The following fields are mandatory when the dataset is part of a series of periodic datasets:

[dcat:inSeries](https://www.w3.org/TR/vocab-dcat-3/#Property:dataset_in_series)
: The URL of a `dcat:DataSeries` which associates this Dataset with the overall series. The DataSeries is created by the publisher and contains their data only.

The following fields are optional:

[dcat:version](https://www.w3.org/TR/vocab-dcat-3/#Property:resource_version)
: Version number of the dataset, this should preferably follow [semantic versioning](https://semver.org/) if possible. Versioning of the dataset should be used to indicate changes in delivery mechanism, or in representation, rather than for changes in the underlying data. For example, this should not be used to differentiate between datasets from different years, rather it should be used to indicate whether a potential data consumer might need to alter how it processes any returned data. 

[dcat:versionNotes](https://www.w3.org/TR/vocab-dcat-3/#Property:resource_version_notes)
: Notes used to explain any changes to this version.


Any additional metadata defined by published Standards may be added.

### Distribution metadata fields

To specify how the data may be downloaded, one or more associated `dcat:Distribution` objects must be included which contain:

[dcat:downloadURL](https://www.w3.org/TR/vocab-dcat-3/#Property:distribution_download_url)
: A stable URL for download of the dataset, subject to access controls specified in the Dataset object. Liveness of the server will be tested by making a HEAD request to this URL.

[dcat:media_type](https://www.w3.org/TR/vocab-dcat-3/#Property:distribution_media_type)
: The MIME type of the download file.

The following fields are optional, but encouraged. They are mandatory for higher assurance and Scheme-conforming data sources.

`ib1:dataSchema`
: The URL of a schema file specifying the format of the downloadable file. The type of schema depends on the `dcat:mediaType`:
`application/json` are documented by JSON Schema files,
`application/xml` by XSD 1.1 files, and
`text/csv` by [CSVW](https://www.w3.org/ns/csvw) files.

### Additional metadata for Datasets and Data Services

The information above is the minimum needed to ensure that a data source can be used by the Trust Framework participants, and is visible in [the Open Net Zero](https://opennetzero.org) search system. There 
are, however, other properties of a dataset which may be useful to potential data consumers. Where such information can 
be provided, it should be provided in as standard a form as possible - in practice this translates to making use of 
existing ontologies such as DCAT and Dublin Core by preference, then shared, industry-specific, ontologies, and only 
using internal or custom representation when absolutely necessary.

Of particular note, and something we would like to ultimately expose in the Open Net Zero search interface, is information about the geospatial and temporal ranges of entries within a dataset. This is a complex subject, but one that has already been handled by DCAT. If you need to express this kind of information, please do so according to the standards laid out 
[here](https://www.w3.org/TR/vocab-dcat-2/#time-and-space).

We encourage use of the `dcat:keyword` list for datasets. These translate to “tags” in our web interface and are useful to group datasets around specific topics.


## Full Example

### Data Service

```
@prefix dcat: <http://www.w3.org/ns/dcat#> . 
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix ib1: <http://registry.ib1.org/ns/1.0/> .

<https://data-provider-example.com/supply-voltage/v0>
    a dcat:DataService ;
    dcterms:title "Electricity Supply Voltage"@en ;
    dcterms:description "API to query supply voltage across the grid"@en ;
    dcterms:publisher <https://registry.ib1.org/member/my-energy-company> ;
    dcterms:conformsTo <https://registry.ib1.org/class/supply-voltage> ; 
    dcat:version "0.1.2" ;
    dcat:endpointDescription <https://registry.ib1.org/api/electricty-voltage> ;
    ib1:heartbeatDescription <https://registry.ib1.org/api/heartbeat-simple> ;
    dcat:endpointURL <https://data-provider-example.com/supply-voltage/v0> ;
    ib1:trustFramework <http://estf.registry.ib1.org> ;
    ib1:datasetAssurance "IcebreakerOne.DatasetLevel1" ;
    ib1:sensitivityClass "IB1-SA" ;
    ib1:permitGroup <https://directory.ib1.org/group/network-operator> ;
    ib1:permitGroup <https://directory.ib1.org/group/report-provider> ;
    dcterms:license <https://creativecommons.org/licenses/by/4.0/> ;
.
```

### Dataset with Distributions and Data Series

```
@prefix dcat: <http://www.w3.org/ns/dcat#> . 
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix ib1: <http://registry.ib1.org/ns/1.0/> .

<https://data-provider-example.com/generation-report/oct2024>
    a dcat:Dataset ;
    dcterms:title "Generation Report Oct 2024"@en ;
    dcterms:description "Data report on generation"@en ;
    dcterms:publisher <https://registry.ib1.org/member/my-energy-company> ;
    dcterms:conformsTo <https://registry.ib1.org/class/generation-report> ; 
    dcat:version "0.1.2" ;
    dcat:inSeries <https://data-provider-example.com/generation-report>;
    dcat:distribution <https://data-provider-example.com/generation-report/oct2024/csv> ;
    dcat:keyword "solar"@en,
	    "electricity"@en,
	    "retrofit"@en ;
    ib1:trustFramework <http://estf.registry.ib1.org> ;
    ib1:datasetAssurance "IcebreakerOne.DatasetLevel1" ;
    ib1:sensitivityClass "IB1-SA" ;
    ib1:permitGroup <https://directory.ib1.org/group/network-operator> ;
    ib1:permitGroup <https://directory.ib1.org/group/report-provider> ;
    dcterms:license <https://creativecommons.org/licenses/by/4.0/> ;
.

<https://data-provider-example.com/generation-report/oct2024/download>
	a dcat:Distribution ;
	dcterms:description "CSV"@en ;
	dcat:downloadURL <https://data-provider-example.com/generation-report/oct2024/csv> ;
	dcat:media_type "text/csv"@en ;
	ib1:dataSchema <https://registry.ib1.org/format/generation-report/v2> ;
.

<https://data-provider-example.com/generation-report>
    a dcat:DatasetSeries ;
    dcterms:title "Generation Reports from My Energy Company"@en ;
.
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzY4MTUyMTUyLC00ODYxODA0NDAsLTE2Nz
c5NDgzNiw0OTE4Njg5NjMsLTE4MzY0ODI1OTIsLTExODU4MjA4
MjMsMzUyNDI5NSwtMTc3Mjk1NTY3OSwtMTUwMzY5NDAwLDU0MD
U3NjUzLC0xMDMyMjMyNTIzLC04NDA2NTUxODksLTU3OTM2NTg2
MCwtMTM2MzYzMTQwMSwtMTQ3MDQzMzM2MywxNzUxMjM0OTkwLC
02MTE3OTM1MTAsMTUxNzk1OTM4OCwxMTg5MzQyMzY2LDM1MTI3
Njc4MF19
-->