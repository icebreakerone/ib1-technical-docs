# Guidance for Data Providers

**NOTE**: This document is primarily intended for technical and operations teams within organisations wishing to participate in the IB1 Trust Framework as [Data Providers](../glossary.md#term-Data-Provider).

**NOTE**: The key words **“MUST”**, **“MUST NOT”**, **“REQUIRED”**, **“SHALL”**, **“SHALL NOT”**, **“SHOULD”**, **“SHOULD NOT”**, **“RECOMMENDED”**, **“MAY”**, and **“OPTIONAL”** in this document are to be interpreted as described in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

## Data Provider Role and Responsibilities

[Data Providers](../glossary.md#term-Data-Provider) are IB1 Trust Framework members which make data sets available to:

* [Data Consumers](../glossary.md#term-Data-Consumer) within the Trust Framework

    * Applies to shared data sets
    * Data [APIs](../glossary.md#term-Application-programming-interface) secured using Financial-grade [API](../glossary.md#term-Application-programming-interface) security ([FAPI](../glossary.md#term-Financial-Grade-API))

* Any third party, in the case of open data

    * Open data sets are made available through publicly accessible [APIs](../glossary.md#term-Application-programming-interface)
    * Data are made available under an appropriate open license agreement

In this context, Data [APIs](../glossary.md#term-Application-programming-interface) can be anything from a simple link to a [CSV](../glossary.md#term-Comma-Separated-Value) or other file (for open data) to a complex query system returning custom output on demand.

To support this role, [Data Providers](../glossary.md#term-Data-Provider) have certain responsibilities:

### Responsibility - Data classification

[Data Providers](../glossary.md#term-Data-Provider) are responsible for classification of their data sets by data sensitivity class, and for ensuring that data are shared, or not shared, as appropriate.

* Any data classed as [OE-C](../glossary.md#term-Data-sensitivity-class-closed) (Closed) or [OE-SP](../glossary.md#term-Data-sensitivity-class-personal) (Personal) **MUST NOT** be shared within the IB1 Trust Framework at present.
* Data in [OE-O](../glossary.md#term-Data-sensitivity-class-open), [OE-SA](../glossary.md#term-Data-sensitivity-class-shared-A), and [OE-SB](../glossary.md#term-Data-sensitivity-class-shared-B) **MAY** be shared within the IB1 Trust Framework as described in the following sections

### Responsibility - Access and licensing specification

[Data Providers](../glossary.md#term-Data-Provider) are responsible for creating access rules for each dataset shared via the IB1 Trust Framework. For each data set, the [Data Provider](../glossary.md#term-Data-Provider) must
create a set of one or more access rules as defined in [Data Set Metadata](../metadata.md#data-set-metadata). These rules specify the conditions under which access will be granted, along with the capabilities forming the license grant should those conditions be satisfied.


* [Data Providers](../glossary.md#term-Data-Provider) **MUST** ensure that access conditions and capability grants are non-discriminatory and fair to Data Consumers

* [Data Providers](../glossary.md#term-Data-Provider) **SHOULD** ensure that the validity time bounds of any published capability grants are sufficient for reasonable commercial operation of a data consumer

### Responsibility - Data provision

[Data Providers](../glossary.md#term-Data-Provider) are responsible for providing a data [API](../glossary.md#term-Application-programming-interface) for each data set, and for configuring and securing each [API](../glossary.md#term-Application-programming-interface) in accordance with the kinds of data it exposes (along with any other access conditions deemed necessary and appropriate by the [Data Provider](../glossary.md#term-Data-Provider) on a per-data-set basis)


* Open data **MUST** be made available with no authentication or authorization requirements


* Shared data **MUST** made available through a [FAPI](../glossary.md#term-Financial-Grade-API) compliant resource server connected to the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service)’s authorization service (see [Common Security Requirements](technical_common.md#common-security-requirements) for more details)

#### Data formats

The IB1 Trust Framework does not define or mandate individual data formats to be returned from data [APIs](../glossary.md#term-Application-programming-interface) - the diversity of kinds of information in the sector renders this impractical, and the additional overhead imposed on data providers would be undesirable.

With this said, we would encourage [Data Providers](../glossary.md#term-Data-Provider) to consider likely automated consumption of data when designing their data [APIs](../glossary.md#term-Application-programming-interface) - this implies using machine readable formats such as [CSV](../glossary.md#term-Comma-Separated-Value), [JSON](../glossary.md#term-Javascript-Object-Notation) and similar, with a preference for those formats compatible with existing software tools and libraries.

### Responsibility - Data integrity and correctness

[Data Providers](../glossary.md#term-Data-Provider) are responsible for the correctness of data returned by their published data [APIs](../glossary.md#term-Application-programming-interface). We plan for the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) or Oopwill provide a
mechanism by which [Data Consumers](../glossary.md#term-Data-Consumer) can report any data quality issues, and will convey any such reports to a nominated contact within the [Data Provider](../glossary.md#term-Data-Provider).

### Responsibility - Metadata provision

[Data Providers](../glossary.md#term-Data-Provider) are responsible for creating, and publishing, metadata for each exposed data set. This provides visibility of each
data set within the Open Energy Governance Service ([OEGS](../glossary.md#term-Open-Energy-Governance-Service)) Registry.

The metadata file covers, for each provided data set, whether shared or open:


* Semantic content


* Access rules and licensing of the data set


* Transport mechanism specification


* Syntactic content

The content and format of the metadata file can be found at [Data Set Metadata](../metadata.md#data-set-metadata).

The [Data Provider](../glossary.md#term-Data-Provider) is responsible for the accuracy and completeness of this metadata.

### Responsibility - API availability

[Data Providers](../glossary.md#term-Data-Provider) are responsible for availability of their published data [APIs](../glossary.md#term-Application-programming-interface). Availability will be monitored automatically by the
[OEGS](../glossary.md#term-Open-Energy-Governance-Service), availability information will form part of the metadata for each data set record in the [OEGS](../glossary.md#term-Open-Energy-Governance-Service) Registry.

The [OEGS](../glossary.md#term-Open-Energy-Governance-Service) will provide a mechanism for [Data Providers](../glossary.md#term-Data-Provider) to announce scheduled downtime when planned, and to report unscheduled
downtime when necessary.

### Responsibility - API stability and change management

[Data Providers](../glossary.md#term-Data-Provider) are responsible for managing any change to the data [APIs](../glossary.md#term-Application-programming-interface) such that disruption to [Data Consumers](../glossary.md#term-Data-Consumer) is minimised. This is handled
through:


* Semantic versioning of all [API](../glossary.md#term-Application-programming-interface) methods


* Publication of anticipated changes and retirement of [API](../glossary.md#term-Application-programming-interface) versions through the [OEGS](../glossary.md#term-Open-Energy-Governance-Service)


* Changeover periods where new and prior [API](../glossary.md#term-Application-programming-interface) versions are run in parallel

## Data API Requirements

Unlike open banking, open energy does not mandate particular [APIs](../glossary.md#term-Application-programming-interface) for data provision - it is expected that there will
be a variety of mechanisms to expose data, with varying inputs (from a single data set [ID](../glossary.md#term-Identification) to a complex query object)
and varying kinds of output dependent on the information exposed.

With that said, there are certain properties that all data [APIs](../glossary.md#term-Application-programming-interface) must satisfy to interoperate successfully with other
parties within the open energy ecosystem.

We refer to endpoints used to retrieve energy data as data endpoints, and others as infrastructure endpoints.

### Date and time formats

Whenever date or time quantities are accepted or returned from a data [API](../glossary.md#term-Application-programming-interface), these values MUST conform to
[|RFC| 3339](https://tools.ietf.org/html/rfc3339). This is referenced elsewhere in this document as **date/time**

### Endpoint security

#### Open data endpoints

Data endpoints which provide access to open data (in class [OE-O](../glossary.md#term-Data-sensitivity-class-open)) **MUST NOT** require any form of authentication
prior to access. This includes allowing access to entities which are not members of the open energy ecosystem.

#### Shared data endpoints

Data endpoints which provide access to shared data (in classes [OE-SA](../glossary.md#term-Data-sensitivity-class-shared-A) and [OE-SB](../glossary.md#term-Data-sensitivity-class-shared-B)) **MUST** implement the subset
of the resource server part of the [FAPI](../glossary.md#term-Financial-Grade-API) specification used within Open Energy as described in
[Common Security Requirements](technical_common.md#common-security-requirements), and authorize against the [OEGS](../glossary.md#term-Open-Energy-Governance-Service) authorization service.

Protected data endpoints **MAY** use the token introspection mechanism provided by [FAPI](../glossary.md#term-Financial-Grade-API) to gather additional
information about the client making the request prior to any access decision.

### Heartbeat and monitoring endpoint

All data [APIs](../glossary.md#term-Application-programming-interface) **SHOULD** include a [FAPI](../glossary.md#term-Financial-Grade-API) protected heartbeat infrastructure endpoint. This serves two purposes:


* It allows the [OEGS](../glossary.md#term-Open-Energy-Governance-Service) to monitor the liveness of the data [API](../glossary.md#term-Application-programming-interface)


* It provides some level of verification that the resource server has been correctly configured

The heartbeat endpoint location is defined within the data set metadata file, if specified it **MUST** respond to
`GET` requests from the [OEGS](../glossary.md#term-Open-Energy-Governance-Service) monitoring system with a `200` status code.

If the heartbeat response contains a body, the body will be interpreted by the [OEGS](../glossary.md#term-Open-Energy-Governance-Service) monitoring system as a [JSON](../glossary.md#term-Javascript-Object-Notation)
dictionary containing statistics for the period between the most recent two successful calls to the heartbeat
endpoint (including the call to which this is a response). This response is **RECOMMENDED** as it provides oversight
of [API](../glossary.md#term-Application-programming-interface) usage to the [OEGS](../glossary.md#term-Open-Energy-Governance-Service).

Legal keys, and the semantics of their associated values, are as follows:

+----------------------------------+------------------------------------------------------------------------------------+
| Name                             | Content                                                                            |
+==================================+====================================================================================+
| `period_start`                   | **date/time** of the start of the period for which statistics are reported         |
+----------------------------------+------------------------------------------------------------------------------------+
| `period_end`                     | **date/time** of the end of the period for which statistics are reported, this     |
|                                  | will typically be the date and time of the heartbeat request                       |
+----------------------------------+------------------------------------------------------------------------------------+
| `api_call_response_[CODE]_count` | integer number of requests to non-heartbeat endpoints within this data             |
|                                  | [API](../glossary.md#term-Application-programming-interface) which resulted in a   |
|                                  | response of type CODE. A distinct key:value pair is sent in the response for each  |
|                                  | distinct [HTTP](../glossary.md#term-HypterText-Transfer-Protocol) status code      |
|                                  | returned.                                                                          |
+----------------------------------+------------------------------------------------------------------------------------+

### API documentation

Data [APIs](../glossary.md#term-Application-programming-interface) **MUST** be described within the transport section of the data set metadata file.

### Versioning

All data [APIs](../glossary.md#term-Application-programming-interface) **MUST** include a version number in the path of each data endpoint. This version SHOULD use semantic
versioning to differentiate between breaking and backwards compatible changes. This **MUST** be documented within the
Open|API| transport section of the metadata file.

## Problem Resolution (Data Providers)

### Effective resolution of problems (Data Providers)

A [Data Provider](../glossary.md#term-Data-Provider) **MUST** create documentation to clearly outline the policies, processes and systems it has in place for problem
resolution and its respective service level objectives. This framework should enable the effective resolution of [Data Consumer](../glossary.md#term-Data-Consumer)
issues and therefore cater for problems that relate specifically to a [Data Consumer](../glossary.md#term-Data-Consumer)’s use of a [Data Provider](../glossary.md#term-Data-Provider)’s data [APIs](../glossary.md#term-Application-programming-interface). In the event that a
[Data Consumer](../glossary.md#term-Data-Consumer) is unable to resolve an issue with a [Data Provider](../glossary.md#term-Data-Provider), the issue **MAY** be flagged to the [OEGS](../glossary.md#term-Open-Energy-Governance-Service) Dispute Resolution function for
independent support.

### Online support

[Data Providers](../glossary.md#term-Data-Provider) **SHOULD** provide [Frequently Asked Questions](../glossary.md#term-Frequently-Asked-Question), which address areas that may be specific to [Data Consumers](../glossary.md#term-Data-Consumer) such as technical advice or test facility
guidance. They should also consider a means of identifying recurring questions or user-error issues so these can be
collated into [Frequently Asked Questions](../glossary.md#term-Frequently-Asked-Question) to support the early resolution of problems.

Problem resolution documentation, [Frequently Asked Questions](../glossary.md#term-Frequently-Asked-Question), contact details, opening times and out of hours support **SHOULD** be published
and easily accessible in one collective area on the [Data Provider](../glossary.md#term-Data-Provider)’s website.

### Ticket management process

[Data Providers](../glossary.md#term-Data-Provider) **MUST** ensure they have a functioning ticket management system which enables them to respond to issues and
problems raised within clearly defined service level targets. A successful problem resolution framework will enable the
efficient identification and resolution of problems which specifically impact [Data Consumers](../glossary.md#term-Data-Consumer). The system for raising and reporting
on tickets should be transparent in order to fully inform users and engender trust across the ecosystem.

### Dispute resolution for access control and capability grant policies (Data Providers)

In cases where a [Data Consumer](../glossary.md#term-Data-Consumer) believes that access conditions or capability grant rules are being applied unfairly, the [OEGS](../glossary.md#term-Open-Energy-Governance-Service)
will act as a mediating party.

### OEGS support (Data Providers)

The [OEGS](../glossary.md#term-Open-Energy-Governance-Service) Service Desk will provide participants with a supplementary ticket management process and supports [Data Providers](../glossary.md#term-Data-Provider) in
communicating problems to ecosystem participants via the noticeboard.

## Change Management

This section outlines various change scenarios that may impact [Data Consumers](../glossary.md#term-Data-Consumer), and provides guidance for a [Data Provider](../glossary.md#term-Data-Provider) to consider when
implementing a change and communicating to [Data Consumers](../glossary.md#term-Data-Consumer).

### Downtime

Planned downtime, by definition, is something that a [Data Provider](../glossary.md#term-Data-Provider) anticipates and therefore is able to give advance notice to [Data Consumers](../glossary.md#term-Data-Consumer).
It is not generally possible to give advance notice of unplanned downtime, but [Data Providers](../glossary.md#term-Data-Provider) should give notice as soon as they
are aware of the downtime.

When providing notifications, [Data Providers](../glossary.md#term-Data-Provider) **SHOULD** provide a specific time period, so [Data Consumers](../glossary.md#term-Data-Consumer) are aware that the data [API](../glossary.md#term-Application-programming-interface) will be
unavailable for that time, or upon a subsequent notification to confirm that the service has been reinstated sooner
than anticipated.

[OEGS](../glossary.md#term-Open-Energy-Governance-Service) Support Services can assist [Data Providers](../glossary.md#term-Data-Provider) with the dissemination of downtime information to the wider Open Energy ecosystem
via its central noticeboard facility.

Planned downtime should be given at least five business days before the event. Apart from cancelling the planned
downtime, no changes should be made to the planned downtime notification within the five business day period. Where
practical, [Data Providers](../glossary.md#term-Data-Provider) should give advance notice via their own website, developer portal or [OEGS](../glossary.md#term-Open-Energy-Governance-Service) of any planned downtime one
calendar month in advance.

### Licensing and access control changes

[Data Providers](../glossary.md#term-Data-Provider) **MUST** provide advance notice of any changes to access control and capability grant policies. This is normally
covered by the time-bounded nature of these grants, but [Data Providers](../glossary.md#term-Data-Provider) **MAY** also use any notification services provided by the [OEGS](../glossary.md#term-Open-Energy-Governance-Service)
to publish additional information about changes.

### Data API changes

[Data Providers](../glossary.md#term-Data-Provider) may periodically wish to upgrade and / or to deprecate versions of their data [APIs](../glossary.md#term-Application-programming-interface). The following
mitigation measures will reduce the impact on service providers of these changes.

#### Dual running and deprecation

[Data Providers](../glossary.md#term-Data-Provider) **SHOULD** support a minimum of two non-compatible [API](../glossary.md#term-Application-programming-interface) versions in a production context, providing both versions
were previously supported by the [Data Provider](../glossary.md#term-Data-Provider), for a period of time long enough to ensure that [Data Consumers](../glossary.md#term-Data-Consumer) have had sufficient time to
successfully test the new version and migrate their applications and customers. [OEGS](../glossary.md#term-Open-Energy-Governance-Service) recommends dual running for at
least six months for a major version, and three months for a minor version. Where a [Data Provider](../glossary.md#term-Data-Provider) implements a data [API](../glossary.md#term-Application-programming-interface) for the
first time, they will only need to support this one version to start with.

The deprecation of unsupported versions is at the [Data Provider](../glossary.md#term-Data-Provider)’s discretion – based on usage metrics. However, the [OEGS](../glossary.md#term-Open-Energy-Governance-Service) may
recommend that any specific version (major, minor, or patch) should be deprecated at any time, and this should be
implemented within three months of notification by the [OEGS](../glossary.md#term-Open-Energy-Governance-Service). This is to cater for critical defects, especially those
relating to security. In exceptional circumstances it may be agreed by [OEGS](../glossary.md#term-Open-Energy-Governance-Service) that support for a specific version is
terminated earlier.

[Data Providers](../glossary.md#term-Data-Provider) must not apply any measures to induce [Data Consumers](../glossary.md#term-Data-Consumer) to adopt a new version of the [APIs](../glossary.md#term-Application-programming-interface) (e.g. rate limiting the older version
while providing better performance on a newer version).

#### API credentials, consent and authorisation

[API](../glossary.md#term-Application-programming-interface) Credentials associated with an [API](../glossary.md#term-Application-programming-interface) should be version agnostic. Therefore, a [Data Consumer](../glossary.md#term-Data-Consumer) accessing v1.0, v1.1 or v2.0 should
be able to use the same [API](../glossary.md#term-Application-programming-interface) Credentials across all available [API](../glossary.md#term-Application-programming-interface) endpoints.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNTI0NzYwMzFdfQ==
-->