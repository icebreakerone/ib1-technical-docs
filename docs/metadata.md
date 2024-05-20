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

`ib1:sensitivityClass`
: The [data sensitivity class](glossary.md#term-Data-sensitivity-class) of this data set. In the current IB1 Trust Framework this should always be one of [IB1-O](glossary.md#term-Data-sensitivity-class-open),  [IB1-SA](glossary.md#term-Data-sensitivity-class-shared-A) or [IB1-SB](glossary.md#term-Data-sensitivity-class-shared-B), no other classes are permitted. The value of this property also determines the level of [API](glossary.md#term-Application-programming-interface) security imposed, with [IB1-O](glossary.md#term-Data-sensitivity-class-open) data sets being open data with no additional security, and the two shared data classes mandating [FAPI](glossary.md#term-Financial-Grade-API) security using the IB1 Trust Framework.

Additional fields will be made mandatory for Scheme-confirming data sources by the Scheme Catalog Requirements Document.

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

## Data Service metadata fields

`dcat:endpointDescription`
: The URL of an OpenAPI file, which fully documents the request parameters and responses, which must be XML or JSON. To allow the OpenAPI file to be used by multiple Data Providers, the file may only contain a single Server object, where the `url` is `"{endpointURL}"`, and `variables` sets the default to `"https://endpointurl-not-specified.ib1.org"`.

`dcat:endpointURL`
: The URL of this specific instances, interpolated with the `endpointURL` variable in the OpenAPI server `url`.

`ib1:heartbeatDescription`
: The URL of an OpenAPI file (with Server specified as `dcat:endpointDescription`), which contains a single Path with a 200 response defined.



## Access Block

This section describes the kinds of licensing, expressed as sets of capabilities, and what, if any, conditions must be 
satisfied before a [data consumer](glossary.md#term-Data-Consumer) can acquire these data.

Each item within this section contains:


1. A statement describing a set of conditions which must be satisfied to grant access, and the set of capabilities 
granted should access be provided by this set of conditions. The exact specification for these statements can be
found at [Access Control and Capability Grant Language](access_control_specification.md#access-control-and-capability-grant-language)


2. A boolean property indicating whether the access conditions in [1] are sufficient (`true`), or simply indicative 
(`false`). In the former case, a [data consumer](glossary.md#term-Data-Consumer) which satisfies all the conditions *will* be granted access, 
in the latter they *may* be granted access, but there may be additional requirements not fully described here


3. A pair of dates indicating the time range for which this access condition is valid. Data providers are encouraged to 
commit to access and license conditions with a reasonable timeframe to allow potential consumers to plan their own
activities

```yaml
access:
  # Access constraint to licensing predicates
  - rule: ib1oe:verified, ib1oe:last_update max_age_days 60 grants ib1oe:use_any
    sufficient: true
    appliesFrom: 20231-04-22
    appliesTo: 20242-04-22
  - rule: group:some_group grants ib1oe:use_any, ib1oe:adapt_any
    sufficient: false
    appliesFrom: 20231-04-22
    appliesTo: 20242-04-22
```

## Transport Block

This section describes the on the wire transport protocol, normally HTTP, but with scope to describe out-of-band 
transports with an initial HTTP negotiation process. It contains at least a single `http` key, the value of which
must be valid [Open|API|](https://swagger.io/specification/) 

For example:

```yaml
transport:
  http:
    # This block is mandatory, and contains the Open|API| spec for the secured or open
    # HTTP endpoints (depending on data class)
    openapi: 3.0.0
    info:
      title: Sample |API|
      description: CSV format data
      version: 0.1.0
    servers:
      - url: http://data-provider-example.com
        description: Describe this particular server if needed
    paths:
      "/data":
        get:
          summary: Returns a CSV containing all the data
          description: If we had any more to describe, we'd do it here
          responses:
            '200':
              description: CSV data stream
```

**NOTE**: Because [API](glossary.md#term-Application-programming-interface) security is defined in relation to the data sensitivity class of the data set, it is not necessary to 
define the security of any presented [API](glossary.md#term-Application-programming-interface) in this section. Data sets in class [IB1OE-O](glossary.md#term-Data-sensitivity-class-open) must expose an [API](glossary.md#term-Application-programming-interface) with no extra
security measures, and those in [IB1OE-SA](glossary.md#term-Data-sensitivity-class-shared-A) and [IB1OE-SB](glossary.md#term-Data-sensitivity-class-shared-B) must be secured by [FAPI](glossary.md#term-Financial-Grade-API) using the IB1 Trust Framework trust services.

### Heartbeat URL

Data providers **SHOULD** create a secured endpoint to act as a heartbeat - if this is specifed then the [TFOEGS](glossary.md#term-Trust-Framework-Governance-Service) will 
periodically call it to assertain liveness and optionally gather metrics as described in
[Heartbeat and monitoring endpoint](ops_guidelines/data_provider_ops_guidelines.md#heartbeat-and-monitoring-endpoint)

A hearbeat URL can be specified as a single key `heartbeat_url` with the value being the fully qualified URL at which 
the hearbeat response is exposed.

## Representation Block

This section describes the format of any data received by a [data consumer](glossary.md#term-Data-Consumer) from this data set. The IB1 Trust Framework does 
not mandate particular formats, so this section is guidance rather than specification.

The only required element in this section is a key `mime` which should contain the 
[media type](https://en.wikipedia.org/wiki/Media_type) of the returned data. At a bare minimum this allows a client to 
load data into some kind of tooling. Depending on this value, other objects may be present.

### text/csv

This type indicates that data is presented in CSV format. In this case, an optional key `csvw` may be defined, and 
should contain valid [JSON-LD](glossary.md#term-JavaScript-Object-Notation-for-Linked-Data) following the [CSV for the Web](https://www.w3.org/TR/tabular-data-primer/) guidelines:

```yaml
representation:
  mime: text/csv
  csvw:
    # This is only applicable if the mime type is text/csv
    "@context": http://www.w3.org/ns/csvw
    tableSchema:
      columns:
        - titles: country
        - titles: country group
        - titles: name (en)
        - titles: name (fr)
        - titles: name (de)
        - titles: latitude
        - titles: longitude
```

### Other types

This is currently open for consultation, we would like to be able to guide data providers towards particular 
representation types for particular kinds of information, and make use of any existing ontologies or standards such as
the [Common Information Model](https://en.wikipedia.org/wiki/Common_Information_Model_(electricity)) where such 
standards will aid interoperability between IB1 Trust FrameworkOpen Energy participants and the wider community.

## Full Example

Putting together all the fragments from previous sections produces the following - this represents a single data set, 
in the full metadata file this would be contained within a list. [YAML](glossary.md#term-YAML-Ain-t-Markup-Language) form:

```yaml
- content:
    "@type": "dcat:Dataset"
    "@context":
      dcat: http://www.w3.org/ns/dcat#
      dct: http://purl.org/dc/terms/
      ib1: http://ib1.org/terms/
    dct:title: My amazing data set
    dct:description: This is a free text description of the data set
    dcat:version: 0.1.2
    dcat:versionNotes: This is a note on this particular version of the dataset
    ib1:sensitivityClass: IB1-SA
    ib1:dataSetStableIdentifier: myData
  access:
    # Access constraint to licensing predicates
    - rule: ib1:verified, ib1:last_update max_age_days 60 grants ib1:use_any
      sufficient: true
      appliesFrom: 20231-04-22
      appliesTo: 20242-04-22
    - rule: group:some_group grants ib1oe:use_any, ib1oe:adapt_any
      sufficient: false
      appliesFrom: 20231-04-22
      appliesTo: 20242-04-22
  transport:
    http:
      # This block is mandatory, and contains the Open|API| spec for the secured or open
      # HTTP endpoints (depending on data class)
      openapi: 3.0.0
      info:
        title: Sample |API|
        description: CSV format data
        version: 0.1.0
      servers:
        - url: http://data-provider-example.com
          description: Describe this particular server if needed
      paths:
        "/data":
          get:
            summary: Returns a CSV containing all the data
            description: If we had any more to describe, we'd do it here
          responses:
            '200':
              description: CSV data stream
  representation:
    mime: text/csv
    csvw:
      # This is only applicable if the mime type is text/csv
      "@context": http://www.w3.org/ns/csvw
      tableSchema:
        columns:
          - titles: country
          - titles: country group
          - titles: name (en)
          - titles: name (fr)
          - titles: name (de)
          - titles: latitude
          - titles: longitude
```

Or, in [JSON](glossary.md#term-Javascript-Object-Notation) form:

```json
[
  {
    "content": {
      "@type": "dcat:Dataset",
      "@context": {
        "dcat": "http://www.w3.org/ns/dcat#",
        "dct": "http://purl.org/dc/terms/",
        "ib1": "http://ib1.org/terms/"
      },
      "dct:title": "My amazing data set",
      "dct:description": "This is a free text description of the data set",
      "dcat:version": "0.1.2",
      "dcat:versionNotes": "This is a note on this particular version of the dataset",
      "ib1:sensitivityClass": "IB1-SA",
      "ib1oe:dataSetStableIdentifier": "myData"
    },
    "access": [
      {
        "rule": "ib1:verified, ib1:last_update max_age_days 60 grants ib1:use_any",
        "sufficient": true,
        "appliesFrom": "20231-04-22T00:00:00.000Z",
        "appliesTo": "20242-04-22T00:00:00.000Z"
      },
      {
        "rule": "group:some_group grants ib1:use_any, ib1:adapt_any",
        "sufficient": false,
        "appliesFrom": "20231-04-22T00:00:00.000Z",
        "appliesTo": "20242-04-22T00:00:00.000Z"
      }
    ],
    "transport": {
      "http": {
        "openapi": "3.0.0",
        "info": {
          "title": "Sample |API|",
          "description": "CSV format data",
          "version": "0.1.0"
        },
        "servers": [
          {
            "url": "http://data-provider-example.com",
            "description": "Describe this particular server if needed"
          }
        ],
        "paths": {
          "/data": {
            "get": {
              "summary": "Returns a CSV containing all the data",
              "description": "If we had any more to describe, we'd do it here"
            },
            "responses": {
              "200": {
                "description": "CSV data stream"
              }
            }
          }
        }
      }
    },
    "representation": {
      "mime": "text/csv",
      "csvw": {
        "@context": "http://www.w3.org/ns/csvw",
        "tableSchema": {
          "columns": [
            {
              "titles": "country"
            },
            {
              "titles": "country group"
            },
            {
              "titles": "name (en)"
            },
            {
              "titles": "name (fr)"
            },
            {
              "titles": "name (de)"
            },
            {
              "titles": "latitude"
            },
            {
              "titles": "longitude"
            }
          ]
        }
      }
    }
  }
]
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDkwMjc4ODQ5LDE1MTc5NTkzODgsMTE4OT
M0MjM2NiwzNTEyNzY3ODAsNTk0OTIxNjY1LDExNDk3NzE3NDAs
LTI1NDI5ODc0OCwyMTI5NjczMzczLDEwMzA5MzM2ODcsLTE5Mj
IxNTkyNTgsMTk2MTM0OTcxMywxNTE5NzU2MDAzLC04NDAyNTg2
OTUsMTIxNTE5NTIxNiwtMTc2ODQxMzMyNl19
-->