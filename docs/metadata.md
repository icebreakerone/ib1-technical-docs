# Data Set Metadata

Each [Data Provider](glossary.md#term-Data-Provider) ([Data Provider](glossary.md#term-Data-Provider)) maintains a set of one or more metadata files, each of which can describe one or more 
distinct data sets. These descriptions serve several purposes:


1. They drive discovery descriptions are ingested into our search system and made available to a [Data Consumer](glossary.md#term-Data-Consumer) 
searching for particular kinds of data.


2. They inform consumption of that data, providing information on:


    1. The [API](glossary.md#term-Application-programming-interface) required to access the data set


    2. Any access constraints which may need to be satisfied


    3. Licenses for any accessed data


    4. Representation and internal semantics of expressions of the data

## Metadata File Structure

**NOTE**: The examples below use [YAML](glossary.md#term-YAML-Ain-t-Markup-Language) format for compactness and increased readability. Data providers may present this 
information either in [YAML](glossary.md#term-YAML-Ain-t-Markup-Language) or in [JSON](glossary.md#term-Javascript-Object-Notation) form.

The overall structure of the metadata file is a list of objects, each of which has the following structure:

```yaml
- content:
    # Discovery information
  access:
    # Access control and licensing information
  transport:
    # |API| information
  representation:
    # Data format information
```

## Content Block

The `content` key contains a block of [JSON-LD](glossary.md#term-JavaScript-Object-Notation-for-Linked-Data) compatible information describing the conceptual content of the dataset. 
A simple example is shown below:

```yaml
- content:
    "@type": "dcat:Dataset"
    "@context":
       dcat: http://www.w3.org/ns/dcat#
       dct: http://purl.org/dc/terms/
       ib1oe: http://icebreakerone.org/ib1energydata.org.uk/oe/terms/
    dct:title: My amazing data set
    dct:description: This is a free text description of the data set
    dcat:version: 0.1.2
    dcat:versionNotes: This is a note on this particular version of the dataset
    ib1oe:sensitivityClass: IB1OE-SA
    ib1oe:dataSetStableIdentifier: myData
```

These are the minimum properties every data set must define, they include terms from the 
[Dublic Core](https://dublincore.org/) (`dct`) and [Data Catalog](https://www.w3.org/TR/vocab-dcat-2/) (`dcat`) 
vocabularies, as well as from the Icebreaker OneOpen Energy core ontology. Prefixes are defined in the [JSON-LD](glossary.md#term-JavaScript-Object-Notation-for-Linked-Data) `@context` object 
as in the example above.

## Mandatory data content metadata fields

+---------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| Key                                                                                                     | Value                                                                                                       |
+=========================================================================================================+=============================================================================================================+
| [dct:title](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/title/)              | Short title for this data set                                                                               |
+---------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| [dct:description](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/description/)  | Longer form description of this data set. This is used in combination with the title and tags when people   |
|                                                                                                         | search for data sets, so aim to include probable search words in the description.                           |
+---------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| [dcat:version](https://www.w3.org/TR/vocab-dcat-3/#Property:resource_version)                           | Version number of the data set, this should preferably follow [semantic versioning](https://semver.org/) if |
|                                                                                                         | possible. Versioning of the data set should be used to indicate changes in delivery mechanism, or in        |
|                                                                                                         | representation, rather than for changes in the underlying data. For example, this should not be used to     |
|                                                                                                         | differentiate between data sets from different years, rather it should be used to indicate whether a        |
|                                                                                                         | potential data consumer might need to alter how it processes any returned data.                             |
+---------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| [dcat:versionNotes](https://www.w3.org/TR/vocab-dcat-3/#Property:resource_version_notes)                | Notes used to explain any changes to this version                                                           |
+---------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| `ib1:sensitivityClass`                                                                                  | The [data sensitivity class](glossary.md#term-Data-sensitivity-class) of this data set. In the current IB1  |
|                                                                                                         | Trust Framework this should always be one of [IB1-O](glossary.md#term-Data-sensitivity-class-open),         |
|                                                                                                         | [IB1-SA](glossary.md#term-Data-sensitivity-class-shared-A), or                                              |
|                                                                                                         | [IB1-SB](glossary.md#term-Data-sensitivity-class-shared-B), no other classes are permitted. The value of    |
|                                                                                                         | this property also determines the level of [API](glossary.md#term-Application-programming-interface)        |
|                                                                                                         | security imposed, with [IB1-O](glossary.md#term-Data-sensitivity-class-open) data sets being open data with |
|                                                                                                         | no additional security, and the two shared data classes mandating                                           |
|                                                                                                         | [FAPI](glossary.md#term-Financial-Grade-API) security using the IB1 Trust Framework.                        |
+---------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| `ib1:dataSetStableIdentifier`                                                                            | An identifier, unique to this [Data Provider](glossary.md#term-Data-Provider), which will not be changed,  |
|                                                                                                         | and which will be used along with the data provider’s own ID to create a unique identifier for this data    |
|                                                                                                         | set within [the Open Net Zero](https://opennetzero.org)                                                     |
+---------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+

### Additional metadata

The information above is the minimum needed to ensure that a data set is visible in [the Open Net Zero](https://opennetzero.org)Energy search system. There 
are, however, other properties of a data set which may be useful to potential data consumers. Where such information can 
be provided, it should be provided in as standard a form as possible - in practice this translates to making use of 
existing ontologies such as DCAT and Dublin Core by preference, then shared, industry-specific, ontologies, and only 
using internal or custom representation when absolutely necessary.

Of particular note, and something we would like to ultimately expose in Open Net Zeroour search interface, is information about the 
geospatial and temporal ranges of entries within a data set. This is a complex subject, but one that has already been 
handled by DCAT. If you need to express this kind of information, please do so according to the standards laid out 
[here](https://www.w3.org/TR/vocab-dcat-2/#time-and-space).

We encourage use of the `dcat:keyword` list for data sets. These translate to “tags” in our web interface and are useful to group data sets around specific topics.

```yaml
dcat:keyword:
  - solar
  - electricity
  - retrofit
```

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
security measures, and those in [IB1OE-SA](glossary.md#term-Data-sensitivity-class-shared-A) and [IB1OE-SB](glossary.md#term-Data-sensitivity-class-shared-B) must be secured by [FAPI](glossary.md#term-Financial-Grade-API) using the Ib1 Trust FrameworkOpen Energy trust services.

### Heartbeat URL

Data providers **SHOULD** create a secured endpoint to act as a heartbeat - if this is specifed then the [TFOEGS](glossary.md#term-Trust-FrameworkOpen-Energy-Governance-Service) will 
periodically call it to assertain liveness and optionally gather metrics as described in
[Heartbeat and monitoring endpoint](ops_guidelines/data_provider_ops_guidelines.md#heartbeat-and-monitoring-endpoint)

A hearbeat URL can be specified as a single key `heartbeat_url` with the value being the fully qualified URL at which 
the hearbeat response is exposed.

## Representation Block

This section describes the format of any data received by a [data consumer](glossary.md#term-Data-Consumer) from this data set. The IB1 Trust FrameworkOpen Energy does 
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
      ib1oe: http://icebreakerone.org/ib1energydata.org.uk/oe/terms/
    dct:title: My amazing data set
    dct:description: This is a free text description of the data set
    dcat:version: 0.1.2
    dcat:versionNotes: This is a note on this particular version of the dataset
    ib1oe:sensitivityClass: IB1OE-SA
    ib1oe:dataSetStableIdentifier: myData
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
        "ib1oe": "http://icebreakerone.org/ib1energydata.org.uk/oe/terms/"
      },
      "dct:title": "My amazing data set",
      "dct:description": "This is a free text description of the data set",
      "dcat:version": "0.1.2",
      "dcat:versionNotes": "This is a note on this particular version of the dataset",
      "ib1oe:sensitivityClass": "IB1|OE-SA|",
      "ib1oe:dataSetStableIdentifier": "myData"
    },
    "access": [
      {
        "rule": "ib1oe:verified, ib1oe:last_update max_age_days 60 grants ib1oe:use_any",
        "sufficient": true,
        "appliesFrom": "20231-04-22T00:00:00.000Z",
        "appliesTo": "20242-04-22T00:00:00.000Z"
      },
      {
        "rule": "group:some_group grants ib1oe:use_any, ib1oe:adapt_any",
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
eyJoaXN0b3J5IjpbLTE3Njg0MTMzMjZdfQ==
-->