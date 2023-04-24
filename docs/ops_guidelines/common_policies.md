# Core Policies

## Introduction (Core Policies)

This section aims to outline core policies and principles with implications for all members of the Icebreaker One Trust Framework. Development of detailed guidance and tooling to accompany the policies in this section is a priority for future development and will be approached openly; using consultation with [Advisory Groups](../glossary.md#term-Advisory-Group), tester organisations and members to ensure that resources meet member needs. All terminology used in this section is outlined in the [Glossary](../glossary.md).

## Metadata

Data sets are described by [Data Providers](../glossary.md#term-Data-Provider) through metadata files. The format for these can be found at [Data Set Metadata](../metadata.md#data-set-metadata)

## Data Sensitivity Classes

The IB1 Trust Framework incorporates a range of categories of data that have varied levels of sensitivity. In order to handle this complexity, and to ensure data is appropriately protected, Icebreaker One has developed a system of data sensitivity classification.

### Policy details

The IB1 Trust Framework operates a system of five data sensitivity classes, graded across three dimensions of sensitivity: personal, commercial, and security. Personal sensitivity considers data defined as ‘personal data’ by the [UK](../glossary.md#term-United-Kingdom) [DPA](../glossary.md#term-Data-Protection-Act) 2018, and related privacy and consumer protection implications. Commercial sensitivity considers intellectual property, risk and commerciality. Security sensitivity includes critical national infrastructure and cybersecurity.

Classes are presented in the table below. A definition, specification and dataset examples for each class is
provided in the IB1 Trust Framework Operational Guidelines. [Data Providers](../glossary.md#term-Data-Provider) assess their datasets using the Operational Guidelines and allocate them to a class, prior to sharing them via the Trust Framework.

Data Sensitivity Classes are designed to supplement, not replace, the [Modernising Energy Data Best Practice Guidance](https://modernisingenergydata.atlassian.net/wiki/spaces/MED/pages/69042178/Data+Best+Practice+latest+release+v0.21)
(Point 12) determining whether data should be made Open, Shared or Closed. In particular, The Data Sensitivity Classes are
designed to provide further nuance to the category of Shared data - identifying three different classes in this space, with different sensitivity profiles.

### Data sensitivity classes in the IB Trust Framework TODO fix this table

+---------------------------+------------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+------------------------+----------------------+
| Data Class                | Description                                                                  | Example Datasets                                              | Personal Sensitivity | Commercial Sensitivity | Security Sensitivity |
+===========================+==============================================================================+===============================================================+======================+========================+======================+
| OE-C                      | Closed data - limited to internal organisational                             | Business-critical proprietary information or IP,              | Very High            | Very High              | Very High            |
|                           | access only or limited, bespoke bilateral contracts                          | critical asset locations, classified information.             |                      |                        |                      |
|                           | under specific circumstances. May be subject to hard                         |                                                               |                      |                        |                      |
|                           | legal barriers to sharing. May be security-critical                          |                                                               |                      |                        |                      |
|                           | information relating to operational technology                               |                                                               |                      |                        |                      |
|                           | supporting critical national infrastructure owned by                         |                                                               |                      |                        |                      |
|                           | an Operator of Essential Services.                                           |                                                               |                      |                        |                      |
|                           |                                                                              |                                                               |                      |                        |                      |
|                           | **Never suitable to share within the IB1 Trust Framework**                         |                                                               |                      |                        |                      |
+---------------------------+------------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+------------------------+----------------------+
| OE-SP                     | Datasets which include personal data, requiring                              | Smart meter data, home temperature preferences,               | Very High            | Medium / High          | Medium / High        |
|                           | appropriate consent to share, or other legal bases                           | protected characteristics or special category data            |                      |                        |                      |
|                           | to data processing, as defined by the                                        | (e.g. dependence on power due to health conditions),          |                      |                        |                      |
|                           | [EU](../glossary.md#term-European-Union)                                     | individual                                                    |                      |                        |                      |
|                           | [GDPR](../glossary.md#term-General-Data-Protection-Regulation)               | [Electric vehicle](../glossary.md#term-Electric-vehicle)      |                      |                        |                      |
|                           | and brought into [UK](../glossary.md#term-United-Kingdom)                    | charging records, transaction data.                           |                      |                        |                      |
|                           | law via the                                                                  |                                                               |                      |                        |                      |
|                           | [DPA](../glossary.md#term-Data-Protection-Act) 2018.                         |                                                               |                      |                        |                      |
|                           |                                                                              |                                                               |                      |                        |                      |
|                           | **Currently not suitable to share within the IB1 Trust Framework                |                                                               |                      |                        |                      |
|                           | with future extensibility subject to consultation.**                         |                                                               |                      |                        |                      |
+---------------------------+------------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+------------------------+----------------------+
| OE-SB                     | Datasets which do not include personal data and which                        | Public                                                        | Medium               | Medium / High          | Medium / High        |
|                           | can/could be shared, but currently require bilateral                         | [Electric vehicle](../glossary.md#term-Electric-vehicle)      |                      |                        |                      |
|                           | contract negotiation. May include data currently shared on the               | charge-point performance, generation asset performance,       |                      |                        |                      |
|                           | basis of group-based, name-based or purpose-limited access.                  | aggregated smart meter data, aggregated, microgeneration      |                      |                        |                      |
|                           | May include aggregated data about individuals, subject to                    | export profiles, ‘Investment grade’ data (e.g. suitable       |                      |                        |                      |
|                           | best practice adherence                                                      | granularity for financial decision-making), sensitive         |                      |                        |                      |
|                           | (e.g. [ICO](../glossary.md#term-Information-Commissioner-s-Office)           | asset data.                                                   |                      |                        |                      |
|                           | anonymisation code.)                                                         |                                                               |                      |                        |                      |
|                           |                                                                              |                                                               |                      |                        |                      |
|                           | **Anonymised data using non-aggregative techniques are currently not         |                                                               |                      |                        |                      |
|                           | suitable to share within this sensitivity class due to complex risks         |                                                               |                      |                        |                      |
|                           | related to individual re-identification. Future extensibility to             |                                                               |                      |                        |                      |
|                           | sharing anonymised data is subject to consultation.**                        |                                                               |                      |                        |                      |
+---------------------------+------------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+------------------------+----------------------+
| OE-SA                     | Shared data - datasets which can/could be shared, but which require the      | Network capacity, outage data, weather predictions,           | Low                  | Medium                 | Low                  |
|                           | user to agree to ‘light touch’ T&Cs to access and use (e.g.                  | European space agency data, daily smart meter                 |                      |                        |                      |
|                           | non-commercial clauses such as those under                                   | installations, geolocation information for non-sensitive      |                      |                        |                      |
|                           |[CC-BY-NC](../glossary.md#term-Creative-Commons-Attribution-Non-commercial)). | assets (e.g. Renewable Assets,                                |                      |                        |                      |
|                           |                                                                              | [EPC](../glossary.md#term-Energy-Performance-Certificate)     |                      |                        |                      |
|                           |                                                                              | certificates).                                                |                      |                        |                      |
+---------------------------+------------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+------------------------+----------------------+
| OE-O                      | Open Data – full open access, under an open data licence. Free to use, by    | [LSOA](../glossary.md#term-Lower-Layer-Super-Output-Areas)    | Very Low             | Very low               | Very Low             |     
|                           | anyone, for any purpose.                                                     | IDs, Digest of [UK](../glossary.md#term-United-Kingdom)       |                      |                        |                      |
|                           |                                                                              | Energy Statistics, regulatory data (e.g. licensing            |                      |                        |                      |
|                           |                                                                              | categories, institutional charters or Terms of Reference,     |                      |                        |                      |
|                           |                                                                              | etc.)                                                         |                      |                        |                      |
+---------------------------+------------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+------------------------+----------------------+

## Data Access Conditions

This policy focuses on **data access**. Data access refers to determining what types of conditions may be specified for Data Consumers to meet in order to gain access to datasets in different sensitivity classes, and how access rules are articulated. This policy has been created with input from the IB1 Trust Framework Advisory Groups, Review Track, and public
consultation responses.

The Trust Framework Governance Service ([TFGS](../glossary.md#term-Trust-Framework-Governance-Service)) is responsible for providing [Data Providers](../glossary.md#term-Data-Provider) with verified information about [Data Consumers](../glossary.md#term-Data-Consumer), in line with specified access conditions for each dataset. However, the [Data Provider](../glossary.md#term-Data-Provider) is solely responsible for determining whether any given [API](../glossary.md#term-Application-programming-interface) request should be honoured (i.e. data access granted), and the licensing terms for any data returned in response to that request. This is due to requirements for control to rest with the [Data Provider](../glossary.md#term-Data-Provider) only.

It is expected that [Data Providers](../glossary.md#term-Data-Provider) will grant access reliably and fairly, in line with the access conditions that they specify. In the event that access is refused, there will be a mechanism for flagging this with the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) for review and dispute management. [Data Providers](../glossary.md#term-Data-Provider) must be able to show clear justification for access refusal. Repeat refusal or non-compliance with specified access conditions may result in penalties (to be determined after Phase 3).

This policy focuses on access conditions for classes [OE-SA](../glossary.md#term-Data-sensitivity-class-shared-A) and [OE-SB](../glossary.md#term-Data-sensitivity-class-shared-B) only. Personal data ([OE-SP](../glossary.md#term-Data-sensitivity-class-personal)) are currently out of scope. Future extensibility of the IB1 Trust Framework to [OE-SP](../glossary.md#term-Data-sensitivity-class-personal) data will be consulted on in future phases of project development.

### Policy details (Data access conditions)

[Data Providers](../glossary.md#term-Data-Provider) will allocate each of their datasets to a sensitivity class prior to sharing them within the IB1 Trust Framework. Data access conditions will then be applied in a manner that is proportionate to the sensitivity profile of each class. We propose to use the data sensitivity classes previously established as a basis for considering access conditions, but not as a complete determinant.

Our approach must serve the goal of reducing friction in sharing  data, while also balancing two distinct sets of needs:

1. [Data Providers](../glossary.md#term-Data-Provider): to retain control over their data.
2. [Data Consumers](../glossary.md#term-Data-Consumer) and [Service Providers](../glossary.md#term-Service-Provider): to access multiple datasets in a clear and manageable way.

As such, we define a standardised range of access condition types as a mechanism to balance the factors outlined above.
This acknowledges the need for more nuance than would be captured under a ‘one size fits all’ approach for each sensitivity class. Instead, our policy enables some tailoring within defined parameters.

The table below describes access conditions for each of the data sensitivity classes. It also demonstrates the rationale for this guidance - identifying the lack of standardised access conditions for [OE-SA](../glossary.md#term-Data-sensitivity-class-shared-A) and [OE-SB](../glossary.md#term-Data-sensitivity-class-shared-B) datasets as a cause of cost and friction in data sharing.

### Data sensitivity classes and access conditions in scope TODO fix table

+------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| Data Class                                                                   | Access Conditions                                                                                       |
+==============================================================================+=========================================================================================================+
| [IB1-C](../glossary.md#term-Data-sensitivity-class-closed)                    | Determined and governed by the [Data Provider](../glossary.md#term-Data-Provider) only.                 |
+------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| [IB1-SP](../glossary.md#term-Data-sensitivity-class-personal)                 | Currently determined by legislation including, but not limited to:                                      |
|                                                                              | [GDPR](../glossary.md#term-General-Data-Protection-Regulation) /                                        |
|                                                                              | [DPA](../glossary.md#term-Data-Protection-Act) 2018, the Data Access and Privacy Framework, and the     |
|                                                                              | Smart Energy Code. [Data Providers](../glossary.md#term-Data-Provider) may also apply additional        |
|                                                                              | non-standard access conditions, such as payment or purpose-based.                                       |
|                                                                              |                                                                                                         |
|                                                                              | Determining access conditions for personal data is not currently in scope       |
|                                                                              | (Future extensibility to be considered |
|                                                                              | based on consultation in due course.                                                                    |
+------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| [IB1-SB](../glossary.md#term-Data-sensitivity-class-shared-B)                 | Currently non-standardised, determined by bilateral contract and bespoke negotiation.                   |
|                                                                              |                                                                                                         |
|                                                                              | Subject of the current policy.                                                                          |
+------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| [IB1-SA](../glossary.md#term-Data-sensitivity-class-shared-A)                 | Currently some standardisation, however bespoke arrangements remain common.                             |
|                                                                              |                                                                                                         |
|                                                                              | Subject of the current policy.                                                                          |
+------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| [IB1-O](../glossary.md#term-Data-sensitivity-class-open)                      | No access conditions - free and accessible to all users.                                                |
+------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+

### IB1 Trust Framework access conditions TODO fix table

+---------------------+---------------------------------------------------------------+----------------------------------------------------------------------+
| Condition domain    | Considerations (examples - not exhaustive)                    | Applicable class                                                     |
+=====================+===============================================================+======================================================================+
| Payment             | Free or paid data                                             | [IB1-SB](../glossary.md#term-Data-sensitivity-class-shared-B) and     |
|                     |                                                               | [IB1-SA](../glossary.md#term-Data-sensitivity-class-shared-A)         |
|                     | Graduated payment rates (e.g. higher granularity)             |                                                                      |
|                     |                                                               |                                                                      |
|                     | One-off or subscription payment rates                         |                                                                      |
+---------------------+---------------------------------------------------------------+----------------------------------------------------------------------+
| Security compliance | [UK](../glossary.md#term-United-Kingdom) Government Minimum   | [IB1-SB](../glossary.md#term-Data-sensitivity-class-shared-B) and     |
|                     | Cybersecurity Standard                                        | [IB1-SA](../glossary.md#term-Data-sensitivity-class-shared-A)         |
|                     |                                                               |                                                                      |
|                     | [UK](../glossary.md#term-United-Kingdom) Government  ‘Secure. |                                                                      | 
|                     | by Design’ IoT guidance                                       |                                                                      |
|                     |                                                               |                                                                      |
|                     | Codes of conduct governing Critical National Infrastructure.  |                                                                      |
+---------------------+---------------------------------------------------------------+----------------------------------------------------------------------+
| Regulatory          | Networks business separation provisions                       | [IB1-SB](../glossary.md#term-Data-sensitivity-class-shared-B) and     |
| compliance          |                                                               | [IB1-SA](../glossary.md#term-Data-sensitivity-class-shared-A)         |
|                     | Competition law                                               |                                                                      |
|                     |                                                               |                                                                      |
|                     | Adherence to section 105 of the Utilities Act 2000            |                                                                      |
+---------------------+---------------------------------------------------------------+----------------------------------------------------------------------+
| Standards           | Meets [MED](../glossary.md#term-Modernising-Energy-Data) Data | [IB1-SB](../glossary.md#term-Data-sensitivity-class-shared-B) and     |
| compliance          | Best Practice Guidance                                        | [IB1-SA](../glossary.md#term-Data-sensitivity-class-shared-A)         |
|                     |                                                               |                                                                      |
|                     | Meets relevant                                                |                                                                      |
|                     | [ISO](../glossary.md#term-Independent-System-Operator)        |                                                                      |
|                     | standards                                                     |                                                                      |
+---------------------+---------------------------------------------------------------+----------------------------------------------------------------------+
| Organisation type   | Local Authorities                                             | [IB1-SB](../glossary.md#term-Data-sensitivity-class-shared-B)         |
|                     |                                                               |                                                                      |
|                     | Energy networks                                               |                                                                      |
|                     |                                                               |                                                                      |
|                     | Schools, colleges and universities                            |                                                                      |
|                     |                                                               |                                                                      |
|                     | Code signatories                                              |                                                                      |
|                     |                                                               |                                                                      |
|                     | Charities                                                     |                                                                      |
|                     |                                                               |                                                                      |
|                     | Specific Open Energy membership tiers (e.g.                   |                                                                      |
|                     | [SME](../glossary.md#term-Small-Medium-Enterprise))           |                                                                      | 
+---------------------+---------------------------------------------------------------+----------------------------------------------------------------------+
| Group membership    | Certain use cases (e.g. community energy project development) | [IB1-SB](../glossary.md#term-Data-sensitivity-class-shared-B)         |
|                     |                                                               |                                                                      |
|                     | Commercial or development partnerships                        |                                                                      |
|                     |                                                               |                                                                      |
|                     | Certain purpose-based groups (e.g. consortium of fuel         |                                                                      |
|                     | poverty-reduction organisations)                              |                                                                      |
|                     |                                                               |                                                                      |
|                     | Social housing retrofit                                       |                                                                      |
|                     |                                                               |                                                                      |
|                     | Public                                                        |                                                                      |
|                     | [Electric vehicle](../glossary.md#term-Electric-vehicle)      |                                                                      |
|                     | charge-point planning                                         |                                                                      |
+---------------------+---------------------------------------------------------------+----------------------------------------------------------------------+
| Other               | Auditing clauses                                              |  [IB1-SB](../glossary.md#term-Data-sensitivity-class-shared-B) and    |
|                     |                                                               |   [IB1-SA](../glossary.md#term-Data-sensitivity-class-shared-A)        |
|                     | Individuals handling the data within a                        |                                                                      |
|                     |  [Data Consumer](../glossary.md#term-Data-Consumer) must.     |                                                                      |
|                     | have completed certain training (e.g.                         |                                                                      |
|                     | [ONS](../glossary.md#term-Office-for-National-Statistics)     |                                                                      |
|                     | Safe Researcher).                                             |                                                                      |
+---------------------+---------------------------------------------------------------+----------------------------------------------------------------------+

### Group based access control

There are two ways in which group-based access can be defined.

1. The group can be externally defined. In this case, an external source provides documentation group membership and duration. For example, a group could be created that encompasses all [UK](../glossary.md#term-United-Kingdom) retail energy suppliers licensed by Ofgem, or the members of a research consortium listed on a particular grant. In both cases, group membership is clearly defined by an external document (e.g. Ofgem licensee list, grant contract) applicable for a defined time period.

2. The group can be self-defined. In this case, documentation of group membership and duration is provided by group members themselves. For example, a set of organisations partnering on a particular use-case or commercial partnership may be able to self-define as a group. Documentation may comprise a project plan or multilateral commercial agreement.

Further policy-development is required to ensure the inclusion of self-defining groups in the IB1 Trust Framework is fair and transparent. Appropriate governance arrangements will also need to be established, for example to prevent confusion for [Data Providers](../glossary.md#term-Data-Provider) or instability associated with too-frequent changes in group creation or membership. As such, it is likely that group-based access defined through authoritative external sources will be explored first in [TFGS](../glossary.md#term-Trust Framework-Governance-Service) development going forward.

### Use case based access control

This type of access condition is difficult to design due to inherent subjectivity in defining the bounds and meaning of
particular use cases. While some [Data Providers](../glossary.md#term-Data-Provider) could be comfortable granting access on the basis of broadly defined use cases, such as fuel poverty reduction, this may not be appropriate to all [Data Providers](../glossary.md#term-Data-Provider) or for more sensitive datasets. 

As such, it is proposed that use case-based access could also be facilitated through the creation of either externally-defined or self-defined groups as outlined above. For example, partners within a Local Authority social housing retrofit project could form a group. This group would be accompanied by information about the specific use case it represents - for example participants, timescale, activities, commercial status etc.) enabling [Data Providers](../glossary.md#term-Data-Provider) to make an informed decision regarding whether to grant access. Any future consideration of access based on more broadly-defined use-cases would be subject to consultation and further policy development.

### Prioritisation

Inclusion of all access conditions outlined above will require significant technical build. In the near future, Icebreaker One may prioritise the establishment of access conditions that industry feedback has indicated take priority. These include: payment, security compliance, regulatory compliance and externally defined groups. As flagged above, in order to maintain robust governance and the IB1 Trust Framework, development of additional access conditions may require further policy work.

## Data Licensing

This policy has been created with input from the IB1 Trust Framework Advisory Groups, Review Track, and public consultation responses. These policies are presented jointly as they unite the processes of determining who can access a particular dataset and what can be done with that dataset. Please note that this policy does not outline draft legal text of the final licences - this is being developed separately with legal support. All ideas outlined in this document remain subject to legal assessment.

### Creating access rules

The previous section on Data Access established a set of concerns (e.g. group-based access, payment-based access etc.)
which may be considered when determining who can access a dataset. To facilitate this policy, we propose a system whereby access and capability grants are determined, for each request to a [Data Provider](../glossary.md#term-Data-Provider)’s [API](../glossary.md#term-Application-programming-interface), on the basis of a set of rules defined and published by that [Data Provider](../glossary.md#term-Data-Provider).

Grants are based on three sources of information:

1. Information from the Trust Framework Governance Service ([TFGS](../glossary.md#term-Open-Energy-Governance-Service)) about the [Data Consumer](../glossary.md#term-Data-Consumer) making the request

2. Information known by the [Data Provider](../glossary.md#term-Data-Provider) (separately from the Trust Framework) about the [Data Consumer](../glossary.md#term-Data-Consumer) making the request, such as customer status, commercial relationships, bilateral agreements, active payments/subscriptions or similar

3. Rules defined by the [Data Provider](../glossary.md#term-Data-Provider) - predicated on information provided by [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) and/or, where necessary to preserve privacy or security, properties known to the [Data Provider](../glossary.md#term-Data-Provider) only

Information provided by [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) to [Data Providers](../glossary.md#term-Data-Provider) can cover two kinds of properties:

* **Inherently true** properties known to the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service), such as:

    * The unique [ID](../glossary.md#term-Identification) of the [Data Consumer](../glossary.md#term-Data-Consumer)

    * The [Data Consumer](../glossary.md#term-Data-Consumer) represents a Local Authority / [SME](../glossary.md#term-Small-Medium-Enterprise) / Enterprise / Community Organisation / Academic group, etc

    * The [Data Consumer](../glossary.md#term-Data-Consumer) has a particular identity such as a registered name


    * The [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) has performed identity assurance to a particular level


* **Transient, time-bounded** properties known to the Trust Framework, such as:

    * The [Data Consumer](../glossary.md#term-Data-Consumer) is a member of a particular scheme, group, or consortium (e.g. a two-year academic research project under a particular named grant)

    * The [Data Consumer](../glossary.md#term-Data-Consumer) has signed a particular document on a particular date (e.g. documentation of a research partnership)

When defining an access rule, [Data Providers](../glossary.md#term-Data-Provider) will also be required to confirm whether the rule is definitive or indicative. Definitive rules stipulate that a [Data Consumer](../glossary.md#term-Data-Consumer) satisfying the stated conditions will be given access. Indicative rules stipulate that a [Data Consumer](../glossary.md#term-Data-Consumer) satisfying the stated conditions may be given access, but there may also be other conditions (e.g. the existence of a payment or bilateral agreement) that must be confirmed by the Data Provider outside the Trust Framework before access is granted. 

If access requests are refused, [Data Providers](../glossary.md#term-Data-Provider) must be able to demonstrate a justifiable reason for doing so. [Data Consumers](../glossary.md#term-Data-Consumer) can challenge access refusals through a dispute-resolution mechanism (part of the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service)) if this is required. Guidance regarding acceptable/unacceptable reasons for access refusal, the dispute-resolution mechanism, and [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) dispute-resolution processes will be developed and published in Phase 4 of the project.

The flow of information associated with access control is shown below - this assumes the [Data Consumer](../glossary.md#term-Data-Consumer) has already acquired an access token from the authorization server. Access control and capability grants are processed on a per-request basis, within the [Data Provider](../glossary.md#term-Data-Provider).

### Associating access rules with capabilities

In the IB1 Trust Framework model, licensing is expressed as the grant of a set of capabilities and associated obligations, scoped to the results of a single [API](../glossary.md#term-Application-programming-interface) call and verified through a non-repudiable digital signature.

This is defined using a rules language, the details of which can be found at [Access Control and Capability Grant Language](../access_control_specification.md#access-control-and-capability-grant-language)

### What are licenses and capabilities?

A data licence is a legal instrument setting out what a [Data Consumer](../glossary.md#term-Data-Consumer) can do with a particular artefact (e.g. dataset). This grants certain ‘capabilities’ to the [Data Consumer](../glossary.md#term-Data-Consumer), comprising a clear expression of things they can do with the artefact. For example, the [CC-BY](../glossary.md#term-Creative-Commons-Attribution) 4.0 Creative Commons licence is highly permissive, granting capabilities such as:

reuse of the licensed artefact for any purpose, redistribution of the artefact, and sharing derivatives of the artefact - so long as the author is credited with the original. 

By contrast, the [CC-BY-ND](../glossary.md#term-Creative-Commons-Attribution-No-derivatives) 4.0 Creative Commons licence grants the capability to reuse the licensed artefact for any purpose, however it does not grant the capability to redistribute derivatives of the artefact.

### How do capability grants work in practice?

Each time a [Data Consumer](../glossary.md#term-Data-Consumer) makes an [API](../glossary.md#term-Application-programming-interface) call, the data returned will be associated with a particular set of capability grants. These can be bound to the data through a non-repudiable digital signature, designed to ensure transparency in the event of any disputes regarding data use. Capability grants will be converted into a licence through the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service). Alongside the legal text of the licence, the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) will make details of capabilities available to [Data Consumers](../glossary.md#term-Data-Consumer) as an easy to understand set of notation/icons. Open Net Zero will also show the license (capabilities and obligations) associated with a dataset in the search results, allowing for searches to be filtered by license in order to promote transparency from the outset.

The IB1 Trust Framework defines a set of common capabilities - [Data Providers](../glossary.md#term-Data-Provider) may create custom capabilities, but we strongly suggest that this should only be done in exceptional cases. The common initial set of capabilities can be found at [Standard capabilities](../access_control_specification.md#standard-capabilities). We propose to use this list as the building blocks for our system of capability grants; whereby the range of capabilities, associated legal text, and ‘human readable’ notation/icons is standardised within the IB1 Trust Framework.

**NOTE**: There is potential for redistribution of derivatives to be managed in more granularity through use of the data pyramid (see Figure 2 below). This could permit [Data Providers](../glossary.md#term-Data-Provider) to specify what level of derivative insights can be passed on (e.g. raw data / results of analysis / recommendations building on analysis).

### Obligations accompanying capability grants

Capability grants will be accompanied by details of any obligations that the [Data Consumer](../glossary.md#term-Data-Consumer) must abide by when exercising a capability. [Data Providers](../glossary.md#term-Data-Provider) must specify any such obligations when associating capabilities with an access rule. As with capabilities, the range of obligations will be standardised within the IB1 Trust Framework and will be included in the digital signature binding the [API](../glossary.md#term-Application-programming-interface) return with the capability grant.

Icebreaker One research has identified a set of common obligations associated with capabilities granted by licences. These include obligations to:

* Credit the author(s) of the original artefact.

* Provide a statement accompanying derivatives works/products/services explaining that the original (credited)
artefact was used in their creation.

* Provide ownership statements for derivative works/products/services.

* License any derivative works/products/services with the same capabilities (‘share-alike’).

* Establish a limit in liability for use of the data in its current state.

We propose to use this list as the building blocks for our system of obligations accompanying capability grants; whereby the range of associations, associated legal text, and ‘human readable’ notation/icons is standardised within the IB1 Trust Framework.

### Why are we proposing this approach?

Constructing a single licence for each dataset, designed to govern all possible scenarios for its use, has to date resulted in the creation of long, complex licensing agreements that are not easily readable by [Data Consumers](../glossary.md#term-Data-Consumer). Industry feedback indicates that this creates friction and costs, for example associated with data-related legal support or accidental misuse of licensed data. These issues are further compounded by growth in the creation of bespoke licences that include non-standard capabilities or legal wording.

Icebreaker One has identified an alternative approach to single data licences, which is currently more commonly used within
data science and software development communities outside of the energy sector. This approach permits dual or multiple licensing of an artefact, whereby the individual licences are kept as simple as possible. For example, dual licensing is commonly used in circumstances where software code is released for free under one licence, then to paying customers under a more permissive licence.

Our approach accepts that a degree of licence pluralism is necessary, and indeed valuable, in supporting a diversity of data types, actors and use-cases within the energy data ecosystem. We are aware that a multiple licensing approach may prompt some concern regarding a risk of licence proliferation and/or opacity. However, our approach can reduce these risks by rationalising and standardising the parameters in which licensing occurs. To do this, Icebreaker One will work to standardise the range of capabilities offered, the legal text governing how these capabilities are expressed, and the ‘human-readable’ ways in which these capabilities are  communicated to [Data Consumers](../glossary.md#term-Data-Consumer). In future, we will further develop guidance for [Data Providers](../glossary.md#term-Data-Provider) encouraging simplicity and discouraging unnecessary protectionism, while also maintaining appropriate protections for higher sensitivity classes of data.

Early feedback from Advisory Groups and critical friends has suggested that benefits of this approach could include
reduced legal, staff and time costs associated with improved searchability, transparency, readability and standardisation of capability grants. By making licensing simpler and faster, it could also help level the digital playing field by offering particular benefits to new, small or ‘public interest’ actors lacking in-house expertise or budget. In the longer term, adoption of this approach could have benefits across the sector as new data markets incentivise [Data Providers](../glossary.md#term-Data-Provider) to align with IB1 Trust Framework standardisation.

### Example access control and capability grant scenarios

**NOTE**: These scenarios have been created to reflect decisions that could be faced by [Data Providers](../glossary.md#term-Data-Provider) in the Open Energy Phase 3 use-case, in which a Local Authority is seeking data to plan the retrofit of social housing with low carbon technologies. Please note that the scenarios are exemplary only and do not necessarily represent the stances of any [Data Providers](../glossary.md#term-Data-Provider) involved in testing.

### Scenario 1

+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Dataset**                | [DNO](../glossary.md#term-Distribution-Network-Operator) capacity/constraint data                                 |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Sensitivity class**      | [OE-SA](../glossary.md#term-Data-sensitivity-class-shared-A)                                                      |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Access control domains** | Access granted to all Open Energy members equally                                                                 |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Access rules**           | `oe:member` unary access condition                                                                                |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Capability grants**      | `oe:member grants oe:use_any`, all [Data Consumers](../glossary.md#term-Data-Consumer) who are members of Open    |
|                            | Energy can access this data set, and receive the right to use for any purpose (see                                |
|                            | [Standard capabilities](../access_control_specification.md#standard-capabilities) for more detail)                |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Obligations**            | Derivatives of the artefact must be accompanied by text stating that the original artefact was used in their      |
|                            | creation. `oe:member grants oe:use_any requires oe:by` (see                                                       |
|                            | [Standard obligations](../access_control_specification.md#standard-obligations) for more detail)                  |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+

### Scenario 2

+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Dataset**                | Public [Electric vehicle](../glossary.md#term-Electric-vehicle) chargepoint use and economic performance profiles |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Sensitivity class**      | [OE-SB](../glossary.md#term-Data-sensitivity-class-shared-B)                                                      |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Access control domains** | Group-based and payment-based access conditions                                                                   |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Access rules**           | Two distinct access constraints:                                                                                  |
|                            |                                                                                                                   |
|                            | 1. `oe:org_type in ['local_authority', 'academic'], provider:customer_level == 1` -  local authorities and        |
|                            | educational institutions are granted access if they are paid customers of the                                     |
|                            | [Data Provider](../glossary.md#term-Data-Provider) at their standard rate                                         |
|                            | 2. `provider:customer_level >= 2` - energy networks are granted access if they are paid customers of the Data     |
|                            | Provider at their large business level                                                                            |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Capability grants**      | In this scenario it would be technically possible for the [Data Provider](../glossary.md#term-Data-Provider)      |
|                            | to apply different capability grants to the two different access rules. In this case the                          |
|                            | [Data Provider](../glossary.md#term-Data-Provider) chooses not to as they have charged commercial entities a      |
|                            | higher access fee and are therefore happy for all [Data Consumers](../glossary.md#term-Data-Consumer) to be       |
|                            | granted the same capabilities. The result is the same set of capabilities (the same licence) is applied to both   |
|                            | access rules.                                                                                                     |
|                            | `oe:org_type in ['local_authority', 'academic'], provider:customer_level == 1 grants oe:use_any`                  |
|                            | `provider:customer_level >= 2 grants oe:use_any`                                                                  |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Obligations**            | The [Data Provider](../glossary.md#term-Data-Provider) chooses the same obligations to be applied to both access  |
|                            | rules                                                                                                             |
|                            | `oe:org_type in ['local_authority', 'academic'], provider:customer_level == 1 grants oe:use_any requires oe:by`   |
|                            | `provider:customer_level >= 2 grants oe:use_any requires oe:by`                                                   |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+

**NOTE**: **Scenario 2**

This more complex scenario detailed above involves a combination of properties known to Open Energy (the market
sector of the [Data Consumer](../glossary.md#term-Data-Consumer) - Local Authority, Educational Institution, or Energy Network) along with properties
which are only known to the [Data Provider](../glossary.md#term-Data-Provider) (the payment status of the [Data Consumer](../glossary.md#term-Data-Consumer)). We can do this because the
rules are evaluated within the [Data Provider](../glossary.md#term-Data-Provider), and not externally within Open Energy’s Governance Service, an entity
which is not aware of any commercial arrangements between the [Data Provider](../glossary.md#term-Data-Provider) and [Data Consumer](../glossary.md#term-Data-Consumer).

### Scenario 3

+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Dataset**                | Solar panel performance data                                                                                      |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Sensitivity class**      |[OE-SB](../glossary.md#term-Data-sensitivity-class-shared-B)                                                       |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Access control domains** | Use case-based and payment-based access conditions                                                                |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Access rules**           | Two rules are created:                                                                                            |
|                            |                                                                                                                   |
|                            | 1. `oe_group:plymouth_lct` - access to use case participants, here defined as a group `lct` managed by `plymouth` |
|                            | (the [ID](../glossary.md#term-Identification) of a local council organisation) and administered using the         |
|                            | [OEGS](../glossary.md#term-Open-Energy-Governance-Service) facilities                                             |
|                            | 2. `provider:customer` - access to all other Open Energy members if they have a paid account with the             |
|                            | [Data Provider](../glossary.md#term-Data-Provider)                                                                |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Capability grants**      | The [Data Provider](../glossary.md#term-Data-Provider) chooses to apply two different capability grants (dual     |
|                            | licences) for the two access rules, reflecting the fact that their dataset is commercially sensitive, therefore   |
|                            | they require payment for its use beyond non-profit or development activities.                                     |
|                            |                                                                                                                   |
|                            | 1. `oe_group:plymouth_lct grants oe:use_dev, oe:use_noncom`                                                       |
|                            | 2. `provider:customer grants oe:use_any, oe:redistribute_combined, oe:combine_any, oe:adapt_any`                  |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+
| **Obligations**            | 1. The original source of the artefact must be credited in all direct uses, derivatives of the artefact must be.  |
|                            | accompanied by text stating that the original artefact was used in their creation, and derivatives must be        |
|                            | licensed under the same terms as the original:                                                                    |
|                            | `oe_group:plymouth_lct grants oe:use_dev, oe:use_noncom requires oe:sa, oe:by`                                    |
|                            | 2. The original source of the artefact must be credited in all direct uses, and derivatives of the artefact       |
|                            | must be accompanied by text stating that the original artefact was used in their creation. There is no            |
|                            | obligation to license derivatives of the artefact under the same terms as the original:                           |
|                            | `provider:customer grants oe:use_any, oe:redistribute_combined, oe:combine_any, oe:adapt_any requires oe:by`      |
+----------------------------+-------------------------------------------------------------------------------------------------------------------+

### Risks of license proliferation

As outlined in previous consultations, the Open Energy data ecosystem is more complex than Open Banking. We are
therefore proposing a different approach to licensing in order to balance a wide range of needs and data types. The
approach further responds to feedback from our Advisory Groups and Review Track that data access and licensing cannot
be served by a one size fits all approach as this would risk restricting the diversity of the ecosystem and potentially
undermining the strength of the trust framework.

We are aware of concerns within the industry that multiple licensing could present risks of licence proliferation,
introducing complexity to the landscape which can act as a barrier for data consumption. Open Energy acknowledges this
risk and presents the following points of response:

> Firstly, some stakeholders have suggested that Open Energy should take a ‘modular approach’ to building a
> ‘single Open Energy licence’. This suggestion outlines a permissive core or standard licence that is presented
> to all [Data Providers](../glossary.md#term-Data-Provider) as the default option for publishing their data. If this is not appropriate for a particular
> dataset, [Data Providers](../glossary.md#term-Data-Provider) would then have the option of adding restrictions (i.e. removing capabilities) by adding
> modular sections of legal text. In practice however, a modular approach doesn’t reduce licence plurality as each
> modification of a licence (e.g. addition of modular text) is viewed legally as the creation of a new licence.
> Open Energy’s approach instead accepts a degree of licence plurality, but will work to standardise the
> discoverability, scope and ease of understanding of that pluralism by offering a limited, standardised and
> searchable range of capabilities. This will be accompanied in due course by guidance for [Data Providers](../glossary.md#term-Data-Provider),
> tailored to each sensitivity class, encouraging as much openness as possible while publishing data safely and
> creating a thriving marketplace.

> Secondly, we acknowledge that the energy data landscape already incorporates a significant degree of licence
> proliferation. For example, it is already common for energy system actors to publish data under bespoke licences
> containing non-standard clauses and/or legal wording. In standardising the range and expression of capabilities,
> Open Energy aims to rationalise some unnecessary forms of licence proliferation in the sector and reduce legal
> costs to [Data Providers](../glossary.md#term-Data-Provider) by reducing the circumstances under which bespoke licences are necessary.

### Is there a risk of licences changing too frequently or without notice?

In any licensing model that is not explicitly time-bound, there is a risk that the [Data Provider](../glossary.md#term-Data-Provider) may choose to change
the licence arbitrarily. We have received feedback that bespoke licensing in the energy sector already produces
insecurity for [Data Consumers](../glossary.md#term-Data-Consumer), who are concerned about the longevity of particular licences in a changeable
environment. For example, an energy forecasting company relies on predictable access to, and capabilities to use, a
range of datasets (e.g. weather data). Changes to the capabilities granted for any of these datasets undermine this
kind of business model, with additional proxy consequences for carbon savings that could be achieved as a result of
better integration of renewable energy generation.

Open Energy aims to address this problem by encouraging [Data Providers](../glossary.md#term-Data-Provider) to indicate the length of time they commit to
retaining the same capability grant for a particular access rule. Although this will be optional, we hope that Data
Providers will be incentivised to do so as this encourages confidence in the market. We are also exploring the
possibility of building a notification system to alert [Data Consumers](../glossary.md#term-Data-Consumer) either to upcoming or new changes in capability
grants to ensure this is done transparently and with adequate warning where possible.

**NOTE**: The time ranges described above are NOT a time limit on the capabilities granted in response to a single request,
it instead specifies a range within which the access rules and their corresponding capability grants will not
change.

Beyond designing positive behavioural and market incentives, it is beyond the scope of Open Energy to control
licence-changes as this remains within the legal rights of the [Data Provider](../glossary.md#term-Data-Provider).

### Where are these rules specified?

The access control, capability, and obligation grants form part of the metadata for a dataset. This is expressed in a
file, hosted and maintained by the [Data Provider](../glossary.md#term-Data-Provider) responsible for the data set. The provisional structure of the entire
file can be found at [Data Set Metadata](../metadata.md#data-set-metadata), in particular the section on the [Access Block](../metadata.md#access-block)

### Where are these rules evaluated, and by whom?

Following our guiding principle that [Data Providers](../glossary.md#term-Data-Provider) remain in control of their data at all times, these rules are
evaluated within the [Data Provider](../glossary.md#term-Data-Provider) [API](../glossary.md#term-Application-programming-interface) implementation. This is necessary to allow for decisions predicated on
information only known to the [Data Provider](../glossary.md#term-Data-Provider), but this could impose additional complexity when setting up and
implementing a [Data Provider](../glossary.md#term-Data-Provider). To mitigate this, we will provide clear specifications and semantics for the rules
language, along with a reference implementation in the Python language.

The current language specification can be found at [Access Control and Capability Grant Language](../access_control_specification.md#access-control-and-capability-grant-language), the time bounds
and other properties form part of the [Access Block](../metadata.md#access-block) specification in the metadata file format.

## Service Desk and Notifications

Open Energy acknowledges industry feedback regarding the need to develop a Service Desk and notifications function.
Developing the full function is beyond the scope of project Phase 3, however it remains an active area for future
development. In the meantime, members will be directed to use a specific email address to catalogue emerging needs and
discuss appropriate [OEGS](../glossary.md#term-Open-Energy-Governance-Service) support. We proposed to use learning from this prototype to inform future service and policy
design.

## Dispute Resolution

Open Energy acknowledges industry feedback regarding the need to develop a dispute resolution function as part of the
[OEGS](../glossary.md#term-Open-Energy-Governance-Service). While developing the full function of dispute resolution falls beyond the scope of Open Energy Phase 3, this
remains an active area for future development. Given the complexity of this topic, ongoing stakeholder engagement and
consultation will be used to shape the future service. In the meantime, members will be requested to use a specific
email address to catalogue any difficulties and discuss appropriate [OEGS](../glossary.md#term-Open-Energy-Governance-Service) support. Learning from this prototype will
inform future service and policy design, alongside consultation activity.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NjUzNTY0NCw5MDM4Mzg4ODddfQ==
-->