# Access Control

Access to data sources is controlled by group membership and licences.

A [catalog entry](metadata.md) specifies one or more groups and a licence. If a participant is a member of any of the groups, they may access the data source under the specified licence.

The Registry maintains a list of the permissions and obligations for access to a data source under a given licence.

Scheme-conforming data sources use [Scheme Catalog Requirements Documents](scheme_catalog_requirements.md) which specify the Access Rules for common formats of data sources.

## Changes from Open Energy

This access control specification is a simplification of Open Energy's access control. Open Energy was designed for one-to-many data products, which required the flexibility for each data provider to describe the individual access requirements for each of their products. Data sharing in a Trust Framework is many-to-many, where the access requirements are set by a sector-wide governance process.

This specification will be iterated as use cases emerge. The current expectation, reflected in this specification, is that the governance process will describe the minimum set of roles permitted to access data under a specific licence, and the data provider may be allowed to expand this to additional roles.

## Example

```
<https://data.example.com/supply-voltage/v0>
    a dcat:DataService ;
	# ...
    ib1:permitGroup <https://directory.estf.ib1.org/scheme/electricity/group/report-provider> ;
    ib1:permitGroup <https://directory.estf.ib1.org/scheme/electricity/group/archiver> ;
    dcterms:license <https://registry.estf.ib1.org/scheme/electricity/licence/voltage-reporting/1.4> ;
.
```

These rules specify that members of either the "Report Provider" and "Archivers" groups may access the data with the Scheme's Voltage Reporting licence.


## Machine readable intepretation of Licences

The Registry maintains an RDF document at a well known URL which maps Licence URLs to Grants (what you are allowed to do with the data) and Obligations (what you must do when providing derivative data to others).

The full legal text of the licence, linked from this RDF document, is the definitive description of what is allowed under this licence.

The document is one or more `ib1:LicenceInterpretation` objects.

```
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix ib1: <http://registry.ib1.org/ns/1.0#>

<https://registry.estf.ib1.org/scheme/electricity/licence/voltage-reporting/1.4>
		a ib1:LicenceInterpretation ;
	dcterms:license https://https://registry.estf.ib1.org/scheme/electricity/licence/voltage-reporting/1.4/legal-text
	ib1:grant ib1:use_any ;
	ib1:grant ib1:adapt_any ;
	ib1:grant ib1:combine_any ;
	ib1:grant ib1:redistribute_original ;
	ib1:grant ib1:combine_external ;
	ib1:obligation ib1:by;
.
```
[dcterms:license](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/terms/license/)
: The URL of the full legal text of the licence.

`ib1:grant`
: The URL of a Grant, with the meaning defined in the contracts which govern the Trust Framework. A consumer may ignore any Grant that they do not understand and use the licence.

`ib1:obligation`
: The URL of an Obligation, with the meaning defined in the contracts which govern the Trust Framework. A consumer __MUST NOT__ use a licence if it includes an Obligation that they do not understand.


## Grants

### Standard grants

These are Grants where the URL prefix is in the IB1 Registry, usually abbreviated as  `ib1:`, indicating that they are defined as part of the Icebreaker One Trust Framework. Data providers **SHOULD NOT**, create their own Grants unless absolutely necessary as doing so acts against the aim of easy interoperability and comprehension of access and licensing rules.

Any additional grants designed **MUST** be within the namespace of the data provider responsible for their definition, and any such data provider **MUST** publish a clear, legally valid, definition of any such permissions. In addition, data providers creating custom permissions **MUST** inform the [TFGS](glossary.md#term-Trust-Framework-Governance-Service) of this, providing links to the aforementioned documentation.

**WARNING**: This section is provisional, the exact final set of base permissions has yet to be determined. Those shown below are a plausible first cut but should not be considered definitive.

+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
| Category                 | Grant name                                | Meaning                                                                                |
+==========================+===========================================+========================================================================================+
| **Use**                  |                                           | **Use the artefact internally**                                                        |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
|                          | `ib1:use_any`                             | For any purpose                                                                        |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
|                          | `ib1:use_dev`                             | For development purposes only (i.e. private or limited development of new              |
|                          |                                           | works, products or services)                                                           |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
|                          | `ib1:use_noncom`                          | For non-commercial purposes only (e.g. education, research, charity work               |
|                          |                                           | etc.)                                                                                  |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
| **Adapt**                |                                           | **Adapt the artefact for internal use**                                                |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
|                          | `ib1:adapt_any`                           | For any purpose                                                                        |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
|                          | `ib1:adapt_dev`                           | For development purposes only (i.e. private or limited development of new              |
|                          |                                           | works, products or services)                                                           |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
|                          | `ib1:adapt_noncom`                        | For non-commercial purposes only (e.g. education, research, charity work               |
|                          |                                           | etc.)                                                                                  |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
| **Combine**              |                                           | **Combine (‘remix’) the artefact**                                                     |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
|                          | `ib1:combine_any`                         | With any other artefacts                                                               |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
|                          | `ib1:combine_external`                    | With other external artefacts                                                          |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
|                          | `ib1:combine_internal`                    | With the Data Consumer’s own products or services                                      |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
| **Redistribute**         |                                           | **Redistribute (‘onward share’ - including to any customers of the Service Provider)** |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
|                          | `ib1:redistribute_original`               | The original artefact                                                                  |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
|                          | `ib1:redistribute_derived`                | Derivatives of the original artefact not produced from other data sets, i.e. filtered  |
|                          |                                           | or cleaned data                                                                        |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
|                          | `ib1:redistribute_combined`               | Derivatives of the artefact produced through artefact combination or use in the Data   |
|                          |                                           | Consumer’s own products or services                                                    |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+

## Obligations

Obligations are constraints on what the data consumer can do with the data, restricting or specialising the meaning of the Grants. They are specified as a URL, similar to Grants.

### Standard obligations

**WARNING**: This set of standard obligations is provisional and may be subject to change

+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
| Obligation               | Name                                      | Explanation                                                                            |
+==========================+===========================================+========================================================================================+
| Fulltext                 | `ib1:ft`                                  | Re-users must display the full text of the license every time they use the work        |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
| Attribution              | `ib1:by`                                  | Re-users must attribute the work to the original source when they use it               |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
| ShareAlike               | `ib1:sa`                                  | Re-users who create derivatives of the work must release the derivatives under the     |
|                          |                                           | same license as the original work, if they choose to distribute the derivatives        |
+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+

**NOTE**: Two additional common constraints in existing (mostly open) licenses are NonCommercial and NoDerivatives. These are explicitly not included here as it is possible to express this through the access conditions (i.e. rather than declaring that a data set is only available for non-commercial usage it is better to say that only non-commercial entities may access it). This is not quite equivalent, but simpler and better defined than the relative minefield of defining ‘non commercial use’.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzk3MzcxNDcxLDg5NjU2NTExMCwxMjAzMj
g3NTI2LC0xNDM5MTg1MTcsMjA1MTEzMzIxMiwyMDA1ODA1NDYw
LDYxMTg1MTc2OCwtODI5OTczNDI3LDE5MTMzMDYxOTIsLTExOD
gxOTk0OTUsLTIxMzk5NDc4NTMsMjA4MDIxODM0LDc0MDExNzQ0
OSwtMjEzMzk3OTQ2MywtNzQxMTM2MDkwLDkzNTA4Mzc0NywtOT
Y5MzAxMjUwLDExNzYxOTA5MDEsLTE5NjkxMzg4MjJdfQ==
-->