# Considerations Before You Start

**NOTE**: This section is designed primarily as a summary tool and should **not** be used in place of more
detailed operational and technical documentation elsewhere in this site.

## Introduction (Before you start)

This section provides ‘at a glance’ lists of items that new members will need to consider in order to meet
operational requirements. It may also be useful for existing members to revisit when they publish ([Data Providers](../glossary.md#term-Data-Provider)) or access
([Data Consumers](../glossary.md#term-Data-Consumer)) a new dataset.

As [Open Energy](../glossary.md#term-Open-Energy) evolves, this section will be updated to form a definitive checklist for compliance. At present however,
it is designed to outline general considerations regarding skills, capabilities and tasks that organisations will
require in order to take part in the [Open Energy](../glossary.md#term-Open-Energy) ecosystem.

The tables below outline considerations for [Data Providers](../glossary.md#term-Data-Provider) and [Data Consumers](../glossary.md#term-Data-Consumer). Each item includes a suggestion of its relevance
to different areas of readiness: commercial, operational, technical, and legal. It is suggested that prospective
members proactively engage teams or staff members with responsibilities for the above four areas of readiness
prior to joining Open Energy as members. Please note that this section is designed to support members to
prepare for data sharing. However, sharing of real data will not commence until the [OEGS](../glossary.md#term-Open-Energy-Governance-Service) goes fully live.

## Considerations for Data Providers

| Consideration

 | Includes

 | Readiness area(s)

 |
| ----------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |  |  |  |  |  |
| Membership contract and fees

                                                              | 
* Contract review by legal counsel


* Contract signature by person with appropriate authority


* Membership fees paid

                                                                                                                                                                                                                                                                                                                                                                        | Legal, commercial

                                                                                                                                                                                                        |
| Onboarding to the Directory

                                                               | 
* Generic contact email addresses and organisation details provided to Open Energy for publishing in the Directory


* Software statement created ([instructions](https://docs.google.com/document/d/1sypYWTeLFSFyfO_zTW6xKCWnao9gKjAo2JHZZIPs2xI/edit?usp=sharing))


* Transport certificate created ([instructions](https://docs.google.com/document/d/1sypYWTeLFSFyfO_zTW6xKCWnao9gKjAo2JHZZIPs2xI/edit?usp=sharing))

                                                                                                                                                                                                                                                                              | Operational, technical

                                                                                                                                                                                                   |
| Metadata file creation

                                                                    | Applies to **all** datasets, both [Open Data](../glossary.md#term-Open-data) and [Shared Data](../glossary.md#term-Shared-data):


* [Metadata](common_policies.md#metadata) file created for each dataset


* Metadata file published and available on a public web server (such as [public GitHub repo](https://github.com/icebreakerone/open-energy-metadata-demo/tree/main/metadata_files))


* Records of the metadata file location created ([instructions](https://docs.google.com/document/d/1sypYWTeLFSFyfO_zTW6xKCWnao9gKjAo2JHZZIPs2xI/edit?usp=sharing))


* Verification that Open Energy automated processes have picked up the file and surfaced contents in [Search](https://openenergy.org.uk)

                                                                                                                   | Technical

                                                                                                                                                                                                                |
| Secure [API](../glossary.md#term-Application-programming-interface) creation and deployment compliant with [Open Energy](../glossary.md#term-Open-Energy) subset of [FAPI](../glossary.md#term-Financial-Grade-API) specification

 | For example, using one of the following methods:


1. Deploy a [Data Provider](../glossary.md#term-Data-Provider) [API](../glossary.md#term-Application-programming-interface) to [EC2](../glossary.md#term-Amazon-Elastic-Cloud-Compute) using the walkthrough [here](https://icebreakerone.github.io/open-energy-python-infrastructure/ec2.html)


2. Use our [Python Support Library](https://icebreakerone.github.io/open-energy-python-infrastructure/) to build
a [Data Provider](../glossary.md#term-Data-Provider) [API](../glossary.md#term-Application-programming-interface) on your own infrastructure


3. Create a [Data Provider](../glossary.md#term-Data-Provider) based on the [FAPI](../glossary.md#term-Financial-Grade-API) subset defined in [Common Security Requirements](technical_common.md#common-security-requirements) using your choice of language
and deployment infrastructure

                                                                                                                            | Technical

                                                                                                                                                                                                                |
| Creation of a rule, or rules, for each dataset and publication of rule(s) in the metadata file

 | 
* Dataset assigned to an Open Energy Sensitivity Class


* [Access rule](../access_control_specification.md#access-control-and-capability-grant-language) or rules created, for each of which:


    * [Data Access Conditions](common_policies.md#data-access-conditions) are specified


    * A grant of [Capabilities](../access_control_specification.md#capabilities) is articulated


    * Any accompanying [Obligations](../access_control_specification.md#obligations) are articulated

                                                                                                                                                                                                                                                     | Operational, commercial, technical

                                                                                                                                                                                       |
| Internal legal sign-off for rules

                                                              | 
* Internal legal advice sought on converting any existing [Shared data](../glossary.md#term-Shared-data) licenses into [Open Energy](../glossary.md#term-Open-Energy)
[Capabilities](../access_control_specification.md#capabilities) and [Obligations](../access_control_specification.md#obligations)


* Internal legal sign-off granted for the creation of all data ‘access rules <Access Control and Capability Grant Language>’

                                                                                                                                                                                                                                 | Legal

                                                                                                                                                                                                                    |
| Skills

                                                                                         | 
* Technical personnel can use Python programming language, or adapt existing [Open Energy](../glossary.md#term-Open-Energy) code and tooling to
alternative language(s) that are used internally


* Technical personnel understand the basics of the [FAPI](../glossary.md#term-Financial-Grade-API) authorization process as described in [Common Security Requirements](technical_common.md#common-security-requirements)

                                                                                                                                                                                                  | Technical

                                                                                                                                                                                                                |
## Considerations for Data Consumers

| Consideration

                                                                                  | Includes

                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Readiness area(s)

                                                                                                                                                                                                        |
| ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Membership contract and fees

                                                                   | 
* Contract review by legal counsel


* Contract signature by person with appropriate authority


* Membership fees paid

                                                                                                                                                                                                                                                                                                                                                                        | Legal, commercial

                                                                                                                                                                                                        |
| Onboarding to the Directory

                                                                    | 
* Generic contact email addresses and organisation details provided to Open Energy for publishing in the Directory


* Software statement created ([instructions](https://docs.google.com/document/d/1sypYWTeLFSFyfO_zTW6xKCWnao9gKjAo2JHZZIPs2xI/edit?usp=sharing))


* Transport certificate created ([instructions](https://docs.google.com/document/d/1sypYWTeLFSFyfO_zTW6xKCWnao9gKjAo2JHZZIPs2xI/edit?usp=sharing))

                                                                                                                                                                                                                                                                              | Operational, technical

                                                                                                                                                                                                   |
| Locate Shared data sets

                                                                        | Use of [Open Energy Search](https://openenergy.org.uk)

                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Operational, technical

                                                                                                                                                                                                   |
| Access [Shared Data](../glossary.md#term-Shared-data)

                                                                             | Methods including one of the following:


1. Use a web-based Python integrated development environment of your choice (e.g. Jupyter-Lab, Google
Collab, or similar) to access and display Shared data ([step-by-step video](https://www.youtube.com/watch?v=CMI2UVdIxFw))


2. Use [Open Energy](../glossary.md#term-Open-Energy)’s Python library to access [Shared data](../glossary.md#term-Shared-data) from your own code
([example](https://icebreakerone.github.io/open-energy-python-infrastructure/service_provider.html))


3. Use tools or languages of your choice to access a [Shared Data](../glossary.md#term-Shared-data) [API](../glossary.md#term-Application-programming-interface).

                                                                                                        | Technical

                                                                                                                                                                                                                |
| Use [Shared data](../glossary.md#term-Shared-data) in compliance with the appropriate licence model

                               | 
* Ensure your organisation - and any individuals handling the data - have a clear understanding of [Open Energy](../glossary.md#term-Open-Energy)
[Capabilities](../access_control_specification.md#capabilities) and [Obligations](../access_control_specification.md#obligations) for the use of datasets


* Gain internal legal sign-off for data use, if applicable


* Payment of related fees to the [Data Provider](../glossary.md#term-Data-Provider) if applicable

For [Data Consumers](../glossary.md#term-Data-Consumer) which are also [Service Providers](../glossary.md#term-Service-Provider):


* Check your understanding of the onward sharing permissions for any data, or derivatives, you are passing
onto your customers.


* Before passing on data or derivatives to your customers, ensure your organisation - and any individuals
handling the data - have a clear understanding of Open Energy capabilities and obligations associated with
onward sharing of data, and of the data pyramid.

 | All

                                                                                                                                                                                                                      |
| Business planning

                                                                              | For [Data Consumers](../glossary.md#term-Data-Consumer) who are [Service Providers](../glossary.md#term-Service-Provider):


* Establish or review your business model for providing services based on, or linked to, data access via [Open Energy](../glossary.md#term-Open-Energy)
in alignment with the agreed capabilities and access controls for the datasets the service will rely on.


* Where a service uses multiple datasets, including those beyond Open Energy, ensure that licences are
compatible to the service being provided and that all licences are appropriately credited.

                                                                                                                                                                                                                                                                       | Commercial

                                                                                                                                                                                                               |
