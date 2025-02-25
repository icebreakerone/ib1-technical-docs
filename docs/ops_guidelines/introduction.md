# Introduction to the Trust Framework

## Overview and purpose of the guidelines

These operational guidelines aim to provide practical advice to all types of actors participating in the IB1 Trust Framework ecosystem. The guidelines are supplemented by links to more detailed technical and membership documentation.

Overarching aims of these operational guidelines:

* To deliver a safe and effective Trust Framework ecosystem that meets the needs of members and supports the broader
sector transition to Net Zero by enabling better discovery and sharing of data via a robust trust framework.

* To support the operational requirements of [Data Providers](../glossary.md#term-Data-Provider) and [Data Consumers](../glossary.md#term-Data-Consumer), stimulating an active data sharing ecosystem. This includes ensuring that all members understand the sensitivity classes, access, and licensing models
for data shared in the ecosystem, and are incentivised towards transparency and interoperability.

* To ensure positive member experiences that demonstrate the [Icebreaker Principles](https://icebreakerone.org/icebreaker-principles/) and encourage them to continue participating in the ecosystem.

* To minimise potential costs associated with insufficient [API](../glossary.md#term-Application-programming-interface) or other technical system testing, downtime, or other common faults.

* To reduce any reputational risks associated with individual members, incorrect application of core policies, or the Icebreaker One ecosystem as a whole.

These guidelines are structured in six sections, outlining:

Introduction (this section): background to the IB1 Trust Framework project, clarifications of the roles and responsibilities of different types of actors operating in the Trust Framework ecosystem.

[Glossary](../glossary.md): definitions of common acronyms, terminology, and technical tools used in the Trust Framework documentation.

[Considerations Before You Start](before_starting.md#considerations-before-you-start): ‘at a glance’ list of items that all types of new members will need
to consider in order to meet operational requirements.

[Core Policies](common_policies.md#core-policies): operational principles and policies central to Trust Framework function. Includes policies governing data sensitivity classification, access controls, and licensing.

[Guidance for Data Consumers](data_consumer_ops_guidelines.md#guidance-for-data-consumers) and [Guidance for Data Providers](data_provider_ops_guidelines.md#guidance-for-data-providers): guidelines outlining how [Data Providers](../glossary.md#term-Data-Provider) can share data safely and securely via the Trust Framework while retaining strong control, provide appropriate and timely metadata, and design safe and effective [APIs](../glossary.md#term-Application-programming-interface) enabling data-sharing. Guidelines outlining how [Data Consumers](../glossary.md#term-Data-Consumer) can meet the requirements for offering data services, access and licensing conditions for different data classes, and best practice with regards to testing, security, ethics and dispute management.

[Additional Material](../additional_material.md#additional-material): links to other relevant documentation (e.g. technical, legal, etc.) sitting outside the operational guidelines.

**Disclaimer**: The contents of the Operational Guidelines do not constitute legal advice. While they have been drafted with regard to relevant regulatory provisions and best practice, they are not a complete list of the regulatory or legal obligations that apply to members and users of the IB1 Trust Framework. Although intended to be consistent with relevant regulations and laws, in the event of any conflict, those regulations and laws will take priority.

Participants are responsible for their own compliance with all applicable regulations and laws, including but not limited to: data protection and privacy, consumer protection laws, and energy sector licences and codes (where applicable). The IB1 Trust Framework operational guidelines will be revised in future in accordance with further development of services offered in the ecosystem, or changes to the regulatory and policy environment in which it operates. Please ensure that you are referring to the most current version of the guidelines prior to reading.

## What is the IB1 Trust Framework, how was it made and who is it for?

The Icebreaker One (IB1) Trust Framework is an ambitious, non-profit project working with across industry, finance, government and regulators to modernise access to data and break down barriers to data sharing. The Trust Framework makes it easier to discover, share, access and use datasets, supporting the drive towards decarbonisation and its related social and economic benefits.

The Trust Framework is a generalisation of the Open Energy project, which received initial development funding from the Modernising Energy Data Access competition, backed by the Office for Gas and Electricity Markets (Ofgem), the Department for Business, Energy and Industrial Strategy ([BEIS](../glossary.md#term-Department-for-Business-Energy-and-Industrial-Strategy)), and [Innovate UK](https://www.gov.uk/government/organisations/innovate-uk). Open Energy in turn built on learning from Open Banking - identifying which elements are transferable to the energy sector, and which require adaptation or fresh thinking. 

Throughout this process, the Icebreaker One team has engaged in extensive consultation with all sectors involved, in order to ensure that the project meets the widest possible variety of needs. The ethos of the IB1 Trust Framework will remain grounded in sector engagement and a collaborative approach as the project moves forward.

The IB1 Trust Framework aims to serve all actors across sectors who are looking to share data, access data, or both.  Membership is open to a wide range of organisations - from large corporations through to charities, researchers, or community groups. Both [Open](../glossary.md#term-Open-data): and [Shared Data](../glossary.md#term-Shared-data) can flow within the Trust Framework.

## How is the IB1 Trust Framework Structured?

The IB1 Trust Framework consists of two core functions: dataset search and discovery, and the Trust Framework Governance Service (TFGS).

These functions are described below.

### Dataset Search

The IB1 Trust Framework’s first core function - [Open Net Zero](https://opennetzero.org) - enables dataset search and discovery. Open Net Zero empowers users to find out what datasets exist and who owns/controls them. Search results also outline the [sensitivity class](common_policies.md#data-sensitivity-classes), [access rules](common_policies.md#data-access-conditions), and [capability grants](common_policies.md#data-licensing) associated with a certain dataset, meaning that access and licensing details are transparent. This works through a search engine designed
specifically to search for datasets, with options to search by different parameters in order to refine results.

It can also be used to discover datasets adjacent to searches; helping users to build up a more rounded picture of the net-zero data landscape in their sphere of interest. Open Net Zero is free, available to all, and will remain so. Access pathways to Open and Shared data are described in the following section.

Datasets provided by IB1 Trust Framework members ([Data Providers](../glossary.md#term-Data-Provider)) and non-Trust Framework members (e.g. web scraped Open Data) may both be visible in Open Net Zero. Datasets provided by an IB1 Trust Framework member will be marked with a badge to indicate that the provenance of the dataset has been verified, uptime is monitored, documentation format is known, and users have a mechanism to provide feedback on the dataset if issues are detected. (Please note that this does not indicate that Icebreaker One has carried out further, more extensive checks on data quality within members’ datasets.)

### Governance Service

The  second core function - the Trust Framework Governance Service ([TFGS](../glossary.md#term-Trust-Framework-Governance-Service)) - supports members to provide, share and access different classes of Shared data (see [Data Sensitivity Classes](common_policies.md#data-sensitivity-classes)) on the basis of preemptive licensing (see [Data Licensing](common_policies.md#data-licensing)). Shared Data accessed via the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) will be provided by Trust Framework members only ([Data Providers](../glossary.md#term-Data-Provider)). The Governance Service aims to provide a secure, trusted mechanism to improve data sharing across the sector by reducing the time and financial costs currently associated with accessing Shared data.

For providers of Shared data, the Governance Service offers a secure and effective way to list datasets and set appropriate access and licensing requirements. For actors wishing to access Shared data, the Governance
Service provides a mechanism to reduce friction and bilateral contract negotiation, even when requesting access to multiple datasets from different providers.

### Project Governance
The IB1 Trust Framework, and Trust Frameworks that build upon it, have a Steering Group (SG) and five Advisory Groups (AGs). The latter may be combined into fewer groups that together cover the function of the five AGs.

#### Steering Group
Provide governance, strategic and tactical leadership, and oversee market-wide communications. Appoint and direct Advisory Groups. Discuss, review and ratify plans.

#### User Needs,  Materiality, Impact Advisory Group
Explore, prioritise and work through **use cases** (identifying users, their needs, mapping the data value chain).

Agree data needs that represent **materiality** of the challenge area that can be linked to **market impact**.
  
Develop the **business, value and impact cases** for the programme and its impact on policy targets, businesses and financial instruments. Where relevant, identify relevant net zero **reporting** standards and frameworks.

#### Technical infrastructure Advisory Group
Agree **technical data and metadata standards** for publishing data, including machine-readable standards and data access (e.g. APIs).
 
Operational **technical systems** that enable data sharing (trust framework) and processing (e.g. calculation).

#### Data Licensing & Legal
Develop standard **legal** data licences that allow restricted data to flow securely across the market, with consent, in alignment with [Data Sensitivity Classes](common_policies.md#Data-Sensitivity-Classes).

This includes key policies, such as conditions for participation, roles and responsibilities.

Outputs of this group address the necessary licences and requirements for a functioning access control.

#### Engagement & Communications
**Convene** and bring people together to ensure common understanding of what is being done, why and how.

Address the user experience (whether business or consumer), signposting and addressing how to inspire behavioural change.

Create **awareness**, **engagement** and **impact** with stakeholders.

#### Policy
Address potential **policy** interventions.

From a business perspective, this may include potential for corporate policy or changes in procurement.

From a government perspective, this may include policy, regulatory or code-based interventions.

#### Group makeup
The membership of these groups is designed to represent a range of different types of organisations, and broader digital sector where relevant. Icebreaker One members can apply to join the Advisory and Steering Groups. However, membership of these groups will not be restricted to members only and non-members may be invited to join in order to balance representation. If you are interested in participating in future Icebreaker One governance mechanisms please contact [info@icebreakerone.org](mailto:info@icebreakerone.org) TODO check this email.

## What data can be found and used through Open Net Zero?

[Open Net Zero](https://opennetzero.org) supports both Open and Shared datasets. Different classes of data, assessed by their levels of sensitivity, are described in [Data Sensitivity Classes](common_policies.md#data-sensitivity-classes).

### Open data

Open data is defined as: ‘Data that anyone can use, for any purpose, for free and is accessible under an Open data licence’. Examples of open datasets include (non-exhaustive): Lower Super Output Layer [ID](../glossary.md#term-Identification) ([LSOA](../glossary.md#term-Lower-Layer-Super-Output-Areas)) data, Digest of [UK](../glossary.md#term-United-Kingdom) Energy Statistics, and OpenStreetMap data.

Open data is visible via Open Net Zero, which is free and open to all users. Open datasets provided by IB1 Trust Framework members ([Data Providers](../glossary.md#term-Data-Provider)) and non-IB1 Trust Framework members will both be visible. There are no barriers to accessing Open data once it is discovered - users are directed to an appropriate [URL](../glossary.md#term-Uniform-Resource-Locator) or [API](../glossary.md#term-Application-programming-interface) to access the data themselves. Open data access is not moderated via the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) as no additional access controls are required.

### Shared data

Shared data is defined as: ‘Data that is neither open nor closed, but can be shared under specific terms and conditions.’ Examples of datasets currently licensed as Shared data include (non-exhaustive): primary substation capacity, network outage data, weather predictions, European space agency data, Electralink daily smart meter installations, certain geolocation information for energy assets and building typologies. As illustrated in these examples, Shared data is extremely diverse and can include datasets with a range of different commercial, personal and security sensitivity levels. To provide nuance in this area, Icebreaker One consultations have established a set of five data sensitivity classes, in which three classes describe separate categories of Shared data.

Due to the sheer diversity of data types, the IB1 Trust Framework does not yet cover all Sensitivity Classes. At present, the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) can facilitate the sharing of non-personal Shared data classes only. This means that currently, sharing of non-aggregated personal data (including datasets using forms of anonymisation other than aggregation conforming to [ICO](../glossary.md#term-Information-Commissioner-s-Office) / [ONS](../glossary.md#term-Office-for-National-Statistics) best practice) is not permitted in the IB1 Trust Framework. Functionality to share personal data (class [IB1-SP](../glossary.md#term-Data-sensitivity-class-personal)), and data that has been anonymised using techniques other than aggregation, are planned for the future subject to further consultation.

The metadata and sensitivity class of Shared datasets are listed on Open Net Zero and are visible to any user. Shared datasets provided by IB1 Trust Framework members ([Data Providers](../glossary.md#term-Data-Provider)) and non-members are both visible (where the latter are known), as described later in this section. Access to Shared datasets provided by IB1 Trust Framework members is moderated through the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service), on the basis of preemptive licensing. Access to Shared data listed on the Search that is not provided by an IB1 Trust Framework member is not supported - users should contact the non-member organisation directly to arrange access.

### Closed data

Closed data is defined as: ‘Data that either cannot be shared or requires a per-use, custom licence negotiated on a case-by-case basis’. Under our current model, closed data is never suitable to share within the IB1 Trust Framework and is not visible through Open Net Zero. While we acknowledge industry feedback flagging potential value in using Open Net Zero infrastructure to privately share Closed data not listed in the Search or [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) Directory, this is not a focus of project development at this time. Any extensibility of this function in future will be subject to consultation.

## What role does your organisation play in the IB1 Trust Framework?

Members of the Trust Framework have different roles: [Data Providers](../glossary.md#term-Data-Provider), [Data Consumers](../glossary.md#term-Data-Consumer), or both. This section outlines the meaning of the different roles and outlines their basic responsibilities.

### [Data Providers](../glossary.md#term-Data-Provider)

[Data Providers](../glossary.md#term-Data-Provider) are organisations that control datasets that they wish to make visible and/or accessible through the IB1 Trust Framework. [Data Providers](../glossary.md#term-Data-Provider) can provide Open and/or Shared datasets. [Data Providers](../glossary.md#term-Data-Provider) are responsible for: data sensitivity classification, creation of access rules, creation of capability grants, data provision, data integrity and correctness, metadata provision, and [API](../glossary.md#term-Application-programming-interface) availability, stability and change management. Full guidance regarding [Data Provider](../glossary.md#term-Data-Provider) responsibilities can be found in [Guidance for Data Providers](data_provider_ops_guidelines.md#guidance-for-data-providers).

### Data Consumers

[Data Consumers](../glossary.md#term-Data-Consumer) are organisations that seek to find and access datasets through the Trust Framework Governance Service (TFGS). [Data Consumers](../glossary.md#term-Data-Consumer) can be established to serve internal organisational needs, to serve external customers, or both. [Data Consumers](../glossary.md#term-Data-Consumer) is a catch-all term referring to all parties accessing data via the [OEGS](../glossary.md#term-Open-Energy-Governance-Service). Full guidance can be found in [Guidance for Data Consumers](data_consumer_ops_guidelines.md#guidance-for-data-consumers)

#### Service Providers

[Data Consumers](../glossary.md#term-Data-Consumer) who access data to serve external customers, potentially including customers outside the IB1 Trust Framework, are categorised as a specific type of [Data Consumer](../glossary.md#term-Data-Consumer) called a [Service Provider](../glossary.md#term-Service-Provider). See [Data Consumer vs Service Provider](data_consumer_ops_guidelines.md#data-consumer-vs-service-provider).

### Dual Roles

Organisations wishing to both provide and access data through the IB1 Trust Framework are able to do so, so long as they fulfill the responsibilities of both roles. [Data Providers](../glossary.md#term-Data-Provider) who do not want to register as [Data Consumers](../glossary.md#term-Data-Consumer), but who wish to access IB1 Trust Framework datasets, are able to do so by using the services of a Service Provider (a type of [Data Consumer](../glossary.md#term-Data-Consumer) in the IB1 Trust Framework that provides services to customers, potentially including non-Trust Framework members).

## How does dataset access and licensing operate under the Trust Framework?

Icebreaker One has consulted publicly and with industry on policies pertaining to: the types of conditions on which data access controls can be based, the process by which [Data Providers](../glossary.md#term-Data-Provider) establish access rules for a dataset, and the model for associating access rules with the grant of particular capabilities and obligations (licensing model).
These policies are outlined briefly below, and set out in full detail in Section 3 of the Operational Guidelines.

### Types of Access Conditions

The IB1 Trust Framework defines a set of conditions which may be specified for [Data Consumers](../glossary.md#term-Data-Consumer) to meet in order to gain access to datasets in different sensitivity classes. These include, but are not limited to: payment, security compliance, regulatory compliance, standards compliance, group-based access, and use case-based access.

### Creating Access Rules (Introduction)

To operationalise Data Access conditions above, the Trust Framework defines a system whereby access grants are determined, for each request to the [API](../glossary.md#term-Application-programming-interface) of a [Data Provider](../glossary.md#term-Data-Provider), on the basis of a set of rules defined and published by that [Data Provider](../glossary.md#term-Data-Provider) in the dataset metadata.

### Data Licensing (Introduction)

A data licence is a legal instrument setting out what a [Data Consumer](../glossary.md#term-Data-Consumer) can do with a particular artefact (e.g.
dataset). This grants certain ‘capabilities’ to the [Data Consumer](../glossary.md#term-Data-Consumer), comprising a clear expression of things they can do with the artefact. Capability grants are accompanied by any obligations that the [Data Consumer](../glossary.md#term-Data-Consumer) must abide by when exercising a capability. The capabilities and obligations associated with each [API](../glossary.md#term-Application-programming-interface) call will be converted into a licence through the Trust Framework Governance Service ([TFGS](../glossary.md#term-Trust-Framework-Governance-Service)).

The IB1 Trust Framework operates through a range of standardised capability grants and obligations. Standardisation includes legal text, ‘human readable’ text and summary notation. [Data Providers](../glossary.md#term-Data-Provider) must specify which capabilities and obligations are associated with each access rule, and publish this transparently in the dataset metadata.

## Future development of the guidelines

The guidelines are designed as an iterative document that will develop in accordance with future phases of the IB1 Trust Framework. If you have any suggestions regarding areas of the operational guidelines that could benefit from further development, please contact [opennetzero@icebreakerone.org](mailto:opennetzero@icebreakerone.org) .
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY0MTc0NTkyOCwxMTc1NDkxNjIxLDExMj
gyODEyODBdfQ==
-->