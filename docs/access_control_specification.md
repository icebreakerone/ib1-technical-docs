# Access Control and Capability Grant Language

Access rules, capability grants, and obligations are explained in [Data Access Conditions](ops_guidelines/common_policies.md#data-access-conditions), this document specifies the
precise syntax and values that can be used.

An access rule contains:


1. Zero or more conditions for access
2. One or more capability grants to the data consumer if access is granted
3. Zero or more obligations falling on the data consumer if access is granted

They are applied to properties of a [Data Consumer](glossary.md#term-Data-Consumer) while processing a request for data from a [Data Provider](glossary.md#term-Data-Provider). These properties can be modelled as a map of names to values; some values may be inferred by joining on the [ID](glossary.md#term-Identification) of the data consumer, some may be directly provided in the [Token introspection](ops_guidelines/technical_common.md#token-introspection) response.


## Permissions

Permission grants for a given set of access conditions are specified as a comma (`,`) separated list of **names**. There **MUST** be at least one **name** in this list, an empty capability grant list is not considered valid.

### Standard permissions

These are permissions where the namespace part of the **name** is `ib1`, indicating that they are defined as part of the Icebreaker One Trust Framework. Data providers **SHOULD NOT**, create their own permissions unless absolutely necessary as doing so acts against the aim of easy interoperability and comprehension of access and licensing rules.

Any additional permissions designed **MUST** be prefixed with the organisation ID of the data provider responsible for their definition, and any such data provider **MUST** publish a clear, legally valid, definition of any such permissions. In addition, data providers creating custom permissions **MUST** inform the [TFGS](glossary.md#term-Trust-Framework-Governance-Service) of this, providing links to the aforementioned documentation.

**WARNING**: This section is provisional, the exact final set of base permissions has yet to be determined. Those shown below are a plausible first cut but should not be considered definitive.

+--------------------------+-------------------------------------------+----------------------------------------------------------------------------------------+
| Category                 | Permission name                           | Meaning                                                                                |
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

### Expressing Open Data licenses with permissions

The permissions defined above in Standard permissions are intended for [shared data](glossary.md#term-Shared-data), but data providers may also publish [open data](glossary.md#term-Open-data). An open data set by definition has no access conditions, so any access rules for such data sets **MUST** have an empty access condition list, and must use one of the following permissions to declare that the data are licensed under a known OSI approved open license

Rules **MUST NOT** grant a mix of permissions in the `open` namespace and permissions in other namespaces, as the semantics of this are not well defined.

+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| Capability name                               | Corresponding open data license                                                                             |
+===============================================+=============================================================================================================+
| `open:cc_by_1.0`                              | [Creative Commons Attribution](https://creativecommons.org/licenses/by/4.0/) (v1.0, v2.0, v2.5, v3.0, v4.0  |
| `open:cc_by_2.0`                              | respectively)                                                                                               |
| `open:cc_by_2.5`                              |                                                                                                             |
| `open:cc_by_3.0`                              |                                                                                                             |
| `open:cc_by_4.0`                              |                                                                                                             |
+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------+
| `open:cc_by_sa_1.0`                           | [Creative Commons Attribution ShareAlike](https://creativecommons.org/licenses/by-sa/4.0/) (v1.0, v2.0,     |
| `open:cc_by_sa_2.0`                           | v2.5, v3.0, v4.0 respectively)                                                                              |
| `open:cc_by_sa_2.5`                           |                                                                                                             |
| `open:cc_by_sa_3.0`                           |                                                                                                             |
| `open:cc_by_sa_4.0`                           |                                                                                                             |
+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------+ 
| `open:cc0`                                    | [Public Domain Dedication](https://creativecommons.org/publicdomain/zero/1.0/) v1.0                         |
+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------+ 
| `open:gfdl_1.1`                               | [GNU Free Documentation License](http://www.gnu.org/copyleft/fdl.html) (v1.1, 1.2, 1.3 respectively)        |
| `open:gfdl_1.2`                               |                                                                                                             |
| `open:gfdl_1.3`                               |                                                                                                             |
+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------+ 
| `open:fal_1.2`                                | [Free Art License](http://artlibre.org/licence/lal/en/) (v1.2, v1.3 respectively)                           |
| `open:fal_1.3`                                |                                                                                                             |
+-----------------------------------------------+-------------------------------------------------------------------------------------------------------------+ 

Open data sets **SHOULD** be released under the latest version of any given license.

## Obligations

Obligations are constraints on what the data consumer can do with the data, restricting or specialising the permissions granted. They are specified as a single **name**.

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
eyJoaXN0b3J5IjpbLTk2OTMwMTI1MCwxMTc2MTkwOTAxLC0xOT
Y5MTM4ODIyXX0=
-->