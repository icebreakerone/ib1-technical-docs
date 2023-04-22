# Guidance for Data Consumers

**NOTE**: This documented is primarily intended for technical and operations teams within organisations wishing to participate in the Icebreaker One Trust Framework as Data Consumers.

**NOTE**: The key words **“MUST”**, **“MUST NOT”**, **“REQUIRED”**, **“SHALL”**, **“SHALL NOT”**, **“SHOULD”**, **“SHOULD NOT”**, **“RECOMMENDED”**, **“MAY”**, and **“OPTIONAL”** in this document are to be interpreted as described in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

## Data Consumer Role and Responsibilities

[Data Consumers](../glossary.md#term-Data-Consumer) are IB1 Trust Framework members that can consume Shared Data (classes [IB1-SA](../glossary.md#term-Data-sensitivity-class-shared-A) and [IB1-SB](../glossary.md#term-Data-sensitivity-class-shared-B) in our [Data Sensitivity Classes](common_policies.md#data-sensitivity-classes)) from [APIs](../glossary.md#term-Application-programming-interface) produced and maintained by [Data Providers](../glossary.md#term-Data-Provider).

In the figure below, we expect [Data Consumers](../glossary.md#term-Data-Consumer) to occupy a number of roles from the lowest in the diagram upwards - they are organisations able to configure their infrastructure (in terms of the consumer parts of the [Common Security Requirements](technical_common.md#common-security-requirements), specifically [Token acquisition](technical_common.md#token-acquisition) and [Token usage - calling a shared data API](technical_common.md#token-usage-calling-a-shared-data-api)). This is covered by the bottom two boxes.

### Data Consumer vs Service Provider

The IB1 Trust Framework does not differentiate between [Data Consumers](../glossary.md#term-Data-Consumer) that access data to solve a problem internal to their organisation and those (known as [Service Providers](../glossary.md#term-Service-Provider)) which offer this as a service to other organisations. A [Data Consumer](../glossary.md#term-Data-Consumer) may also be a [Data Provider](../glossary.md#term-Data-Provider), the roles are not mutually exclusive.

In a similar vein, it would be entirely normal for a [Data Consumer](../glossary.md#term-Data-Consumer) to also access [Open Data](../glossary.md#term-Open-data), and to use [Open Net Zero](https://opennetzero.org) to locate data sets of interest, both open and shared.

### Responsibility - Data consumption

The definition of a [Data Consumer](../glossary.md#term-Data-Consumer) is that it consumes data from [shared data](../glossary.md#term-Shared-data) [APIs](../glossary.md#term-Application-programming-interface). To do this, the organisation **MUST** create cryptographic key material, and maintain a record within the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) directory. It is responsible for the integrity of this key material, and **MUST** put appropriate policies in place to ensure that this material is not misused.

### Responsibility - Data licensing

[Data Consumers](../glossary.md#term-Data-Consumer) are responsible for honouring the licenses for any data obtained through [shared data](../glossary.md#term-Shared-data) [APIs](../glossary.md#term-Application-programming-interface). Where the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) provides technical measures such as cryptographically signed receipts binding data and license conditions together, the [Data Consumer](../glossary.md#term-Data-Consumer) is responsible for retaining and storing such receipts.

## Problem Resolution (Data Consumers)

### Effective resolution of problems (Data Consumers)

We encourage [Data Consumers](../glossary.md#term-Data-Consumer) to direct any problems with data [APIs](../glossary.md#term-Application-programming-interface) first to the [Data Provider](../glossary.md#term-Data-Provider) concerned. In the event that a [Data Consumer](../glossary.md#term-Data-Consumer) is unable to resolve an issue with a [Data Provider](../glossary.md#term-Data-Provider), the issue MAY be flagged to the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) Dispute Resolution function for independent support.

### Dispute resolution for access control and capability grant policies

In cases where a [Data Consumer](../glossary.md#term-Data-Consumer) believes that access conditions or capability grant rules are being applied unfairly, the [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) will act as a mediating party.

### TFGS support

The [TFGS](../glossary.md#term-Trust-Framework-Governance-Service) Service Desk will provide participants with a supplementary ticket management process and supports [Data Consumers](../glossary.md#term-Data-Consumer) in communicating problems to ecosystem participants via the noticeboard.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2Mjk4MTEzNTIsNzI3NTYwNDMxXX0=
-->