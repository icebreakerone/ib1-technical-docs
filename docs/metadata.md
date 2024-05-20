# Dataset & Data Service Metadata

Each [Data Provider](glossary.md#term-Data-Provider) maintains a set of one or more metadata files, each of which can describe one or more 
distinct sources of data. These descriptions serve several purposes:


1. They drive discovery descriptions are ingested into our search system and made available to a [Data Consumer](glossary.md#term-Data-Consumer) 
searching for particular kinds of data.


2. They inform consumption of that data, providing information on:


    1. The [API](glossary.md#term-Application-programming-interface) required to access the data set


    2. Any access constraints which may need to be satisfied


    3. Licenses for any accessed data


    4. Representation and internal semantics of expressions of the data

## Dataset or Data Service?

A Dataset:
* is provided as one or more downloadable files, and
* may be updated periodically.

A Data Service:
* is an API to query some data which uses parameters to specify a subset of data, including time period,
* is specified formally by a machine readable API description, and
* may require consent from a data subject external to the Trust Framework.

They are described by slightly different information in metadata files.

## Scheme-conforming

A Scheme-conforming Dataset or Data Service meets a common standard across a Scheme to provide the same format and meaning of data across all Data Providers. This standard includes the format of the data or API, and the role who can access it under which licenses.

These requirements are published by the Scheme Registry as machine readable Scheme Catalog Requirements Documents, and metadata files link to them to show their conformance.

Most Datasets and Data Services are Scheme-conforming. A Data Provider may publish data which is not Scheme-conforming to use the Trust Framework access control to share ad-hoc data amongst Trust Framework participants, and the Catalog to include Open Data in a public index.

## Metadata File Structure

The metadata is a standard [DCAT](https://www.w3.org/TR/vocab-dcat-3/) RDF file representing one or more sources of data. 

**NOTE**: The examples below use the [Turtle](https://www.w3.org/TR/turtle/) format for compactness and increased readability. Data providers may present this 
information in Turtle, RDF/XML, JSON-LD or N3 formats.

Datasets are represented as Dataset DCAT objects with one or more Distributions. If the data measures the same thing over periods of time, then these must be linked together with a Data Series object. The format of the data is described by JSON Schema, XSD 1.1 or CSVW schemas.

Data Services are represented as Data Service DCAT objects, with OpenAPI specifications of the API and the format of the data in the responses.

The URL of the DCAT object inside the RDF representation is the stable identifer of the Dataset or Data Service. This must remain constant each time the metadata file is fetched and over updates to the metadata.

## Mandatory metadata fields

[dcterms:title](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/title/)
: Short title for this data set

[dcterms:publisher](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/publisher/)
: The URL of the Data Provider's record in the Scheme Directory.

`ib1:sensitivityClass`
: The [data sensitivity class](glossary.md#term-Data-sensitivity-class) of this data set. In the current IB1 Trust Framework this should always be one of [IB1-O](glossary.md#term-Data-sensitivity-class-open),  [IB1-SA](glossary.md#term-Data-sensitivity-class-shared-A) or [IB1-SB](glossary.md#term-Data-sensitivity-class-shared-B), no other classes are permitted. The value of this property also determines the level of [API](glossary.md#term-Application-programming-interface) security imposed, with [IB1-O](glossary.md#term-Data-sensitivity-class-open) data sets being open data with no additional security, and the two shared data classes mandating [FAPI](glossary.md#term-Financial-Grade-API) security using the IB1 Trust Framework.

Additional fields will be made mandatory for Scheme-confirming data sources by the Scheme Catalog Requirements Document.

## Conformance and access control metadata fields

`dcterms:conformsTo`
: The URL of a Scheme Catalog Requirements Document in the Scheme Registry. Most metadata files will include this field.

`ib1:access`
: A list of [`ib1:AccessRule`](access_control_specification.md) bnodes which specify Groups of participants which may access this data, and the Licence under which they can access it.

## Data Service metadata fields

`dcat:endpointDescription`
: The URL of an OpenAPI file, which fully documents the request parameters and responses, which must be XML or JSON. To allow the OpenAPI file to be used by multiple Data Providers, the file may only contain a single Server object, where the `url` is `"{endpointURL}"`, and `variables` sets the default to `"https://endpointurl-not-specified.ib1.org"`.

`dcat:endpointURL`
: The URL of this specific instances, interpolated with the `endpointURL` variable in the OpenAPI server `url`.

`ib1:heartbeatDescription`
: The URL of an OpenAPI file (with Server specified as `dcat:endpointDescription`), which contains a single Path with a 200 response defined.

Additional metadata may be added.

## Dataset metadata fields

As Datasets will be discovered by browsing an index, they need additional metadata for discovery. The following fields are mandatory:

[dcterms:description](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/description/)
: Longer form description of this data set. This is used in combination with the title and tags when people search for data sets, so aim to include probable search words in the description.

[dcat:version](https://www.w3.org/TR/vocab-dcat-3/#Property:resource_version)
: Version number of the data set, this should preferably follow [semantic versioning](https://semver.org/) if possible. Versioning of the data set should be used to indicate changes in delivery mechanism, or in representation, rather than for changes in the underlying data. For example, this should not be used to differentiate between data sets from different years, rather it should be used to indicate whether a potential data consumer might need to alter how it processes any returned data. 

[dcat:versionNotes](https://www.w3.org/TR/vocab-dcat-3/#Property:resource_version_notes)
: Notes used to explain any changes to this version.

### Distribution metadata fields

To specify how the data may be downloaded, one or more associated `dcat:Distribution` objects must be included which contain:

[dcat:downloadURL](https://www.w3.org/TR/vocab-dcat-3/#Property:distribution_download_url)
: A stable URL for download of the dataset, subject to access controls specified in the Dataset object. Liveness of the server will be tested by making a HEAD request to this URL.

[dcat:media_type](https://www.w3.org/TR/vocab-dcat-3/#Property:distribution_media_type)
: The MIME type of the download file.

`ib1:dataSchema`
: The URL of a schema file specifying the format of the downloadable file. The type of schema depends on the `dcat:mediaType`:
`application/json` are documented by JSON Schema files,
`application/xml` by XSD 1.1 files, and
`text/csv` by [CSVW](https://www.w3.org/ns/csvw) files.

### Additional metadata for Datasets

The information above is the minimum needed to ensure that a data set is visible in [the Open Net Zero](https://opennetzero.org) search system. There 
are, however, other properties of a data set which may be useful to potential data consumers. Where such information can 
be provided, it should be provided in as standard a form as possible - in practice this translates to making use of 
existing ontologies such as DCAT and Dublin Core by preference, then shared, industry-specific, ontologies, and only 
using internal or custom representation when absolutely necessary.

Of particular note, and something we would like to ultimately expose in the Open Net Zero search interface, is information about the geospatial and temporal ranges of entries within a data set. This is a complex subject, but one that has already been handled by DCAT. If you need to express this kind of information, please do so according to the standards laid out 
[here](https://www.w3.org/TR/vocab-dcat-2/#time-and-space).

We encourage use of the `dcat:keyword` list for data sets. These translate to “tags” in our web interface and are useful to group data sets around specific topics.

```
dcat:keyword "solar"@en, "electricity"@en, "retrofit"@en ;
```


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
    ib1:sensitivityClass "IB1OE-SA" ;
    ib1:dataSetStableIdentifier: "MYENERGYCOMPANY/DS188" ;
    ib1:access [ a ib1:AccessRule ;
        ib1:group "group1" ;
        ib1:group "group2" ;
        ib1:licence "https://creativecommons.org/licenses/by/4.0/" ;
    ];
.
```

### Dataset with Distributions and Data Series

```
@prefix dcat: <http://www.w3.org/ns/dcat#> . 
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix ib1: <http://registry.ib1.org/ns/1.0/> .

<https://data-provider-example.com/generation-report/oct2024>
    a dcat:Dataset ;
    dcterms:title "Generation Report"@en ;
    dcterms:description "Data report on generation"@en ;
    dcterms:publisher <https://registry.ib1.org/member/my-energy-company> ;
    dcterms:conformsTo <https://registry.ib1.org/class/generation-report> ; 
    dcat:version "0.1.2" ;
    dcat:distribution <```
https://data-provider-example.com/generation-report/oct2024
`
    ib1:sensitivityClass "IB1OE-SA" ;
    ib1:dataSetStableIdentifier: "MYENERGYCOMPANY/DS9871/OCT2024" ;
    ib1:access [ a ib1:AccessRule ;
        ib1:group "group2" ;
        ib1:group "group8" ;
        ib1:licence "https://creativecommons.org/licenses/by/4.0/" ;
    ];
.
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkwMDM3NDQ3NSwxNzUxMjM0OTkwLC02MT
E3OTM1MTAsMTUxNzk1OTM4OCwxMTg5MzQyMzY2LDM1MTI3Njc4
MCw1OTQ5MjE2NjUsMTE0OTc3MTc0MCwtMjU0Mjk4NzQ4LDIxMj
k2NzMzNzMsMTAzMDkzMzY4NywtMTkyMjE1OTI1OCwxOTYxMzQ5
NzEzLDE1MTk3NTYwMDMsLTg0MDI1ODY5NSwxMjE1MTk1MjE2LC
0xNzY4NDEzMzI2XX0=
-->