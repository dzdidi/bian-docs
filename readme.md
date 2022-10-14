#Users (case study available):
[Case studies](https://bian.org/deliverables/case-studies/)
[Implementation Exmaples](https://bian.org/wp-content/uploads/2021/03/BIAN_Implementation_Examples_v1.pdf)

- [ABSA bank](https://bian.org/wp-content/uploads/2021/03/BIAN_Implementation_Examples_v1.pdf#%5B%7B%22num%22%3A113%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C0%2C540%2C0%5D)
- [CC and C Soultions](https://bian.org/deliverables/case-studies/cc_c/)
- [CIBC](https://bian.org/wp-content/uploads/2021/03/BIAN_Implementation_Examples_v1.pdf#%5B%7B%22num%22%3A193%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C0%2C540%2C0%5D)
- [Discover Model Bank](https://bian.org/wp-content/uploads/2021/05/Discover-Model-Bank-as-of-15-May-2017.pdf)
- [PNC bank](https://bian.org/wp-content/uploads/2021/03/BIAN_Implementation_Examples_v1.pdf#%5B%7B%22num%22%3A101%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C0%2C540%2C0%5D)
- [Santander](https://bian.org/wp-content/uploads/2021/03/BIAN_Implementation_Examples_v1.pdf#%5B%7B%22num%22%3A186%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C0%2C540%2C0%5D)
- [SPD](https://bian.org/wp-content/uploads/2021/03/BIAN_Implementation_Examples_v1.pdf#%5B%7B%22num%22%3A145%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C0%2C540%2C0%5D)
- [Virusa](https://bian.org/wp-content/uploads/2021/10/Virtusa-BIAN-for-Sibos-21.pdf)
- [Zafin](https://bian.org/news-room/bian-in-the-news/member-news-zafin-bian/)
- [TCS](https://bian.org/wp-content/uploads/2021/09/BIAN-Powering-purpose-driven-future-ready-banks.pdf)
- [Cognizant](https://bian.org/wp-content/uploads/2021/08/Core-Banking-Modernization-Using-BIAN.pdf)
- Archi Banking Group

#Technologically backed by:
- IBM https://www.ibm.com/support/pages/bian-mappings-ibm-banking-process-and-service-models
- Redhat https://www.redhat.com/en/resources/build-digital-foundation-coreless-banking-overview

#Size:
- 250+ Assets
- 19 Functional Patterns
- 17 Action Terms

#Structure:
BIAN Service Landscape consists of ~320 Service Domains. Grouped in Busiess Areas which in turn consist of Business
Domains. A Service Domain is a conceptual functional design that can be mapped/related to a major application module.
Each service domain contains exactly 1 Asset. Combination of Asset and Functional Patter creates Control Record.

**Function Patters** can also be represented with 1-to-1 mapping to Generic Artifacts (just a  more tech terms) which can
be mapped to Behaviour Qualifiers (even more concrete items).

> For example: Function Patter "Track" -> Generic Artifact "Log Record" -> Behaviour Qualifiers "Event"

Which are fine to devide in Qualifiers but they are out of BIAN scope.


**Action Term** Every Service Domain offers a collection of service operations and usually consumes or ‘delegates’ by
calling the service operations of other Service Domains as needed to complete its work.
(Action Terms are like inteface methods, and BIAN provides mapping to REST specification)

**BIAN provides default mapping table for Functional Patter - to - Action Term**

Service Operation - applicable Action Term and optionally a Behavior Qualifier.

Service Domain properties:
* a discrete business functional partition (not a process step)
* peer collection covers all business activity (elemental)
* acts as an operational service center
* can combine people, procedures & systems
* capable of being outsourced (one ‘sizing’ test)
* does ‘something’ to ‘something’ for the full life-cycle
* handles single or multiple instances for a short or long life-span


# Implementation guidance

> Having both the dynamic (business scenario) and static (wireframe) models of the area of interest is useful to fully
understand the service-centered design for the technical leads and architects.

[Addoption guide](https://view.ceros.com/hotwirepr/bian-guide-to-adoption/p/1)

## Mapping to REST

[APIs](https://bian.org/semantic-apis/)

To define BIAN Semantic APIs each default BIAN Service Domain service operation is matched to a ‘REST endpoint’
description. The scope/purpose of each individual BIAN Service Operation and its associated REST endpoint description
is defined by three concerns:
* The Service Domain’s core functionality
* The service operation action term
* Optionally the Behavior Qualifier

There are several design properties that need to be reflected in the Service Domain specifications to support a fully
event driven design. Some example considerations are (in no specific order):
* Semantic Vocabulary Agreed to Required Precision – all exchanged semantic information must be defined as specific
changes to the value of this information will often be a service triggering factor;
* State Management & Service Triggering – comprehensive event profiles for the Service Domains and their service
triggering logic. This should include configuring thresholds and policies. These can be linked to key information
attributes or with control record and control record partitions as defined by the behavior qualifier type;
* Service Operation Agreements and Policies – this includes more detailed service make-up definitions, including
cross-referencing the policies and thresholds governing/triggering service exchanges as well as the required service
performance, information integrity and security control features
* Transactional, Control, and Referential Exchanges – the required Service Domain information exchanges need to capture
all transactional business activity, management command and control interactions and the background synchronization of
shared reference information
* Defensive Operations – the Service Domain service operation implementation must always handle delayed/erroneous
requests and respond in a graceful/defensive manner
* Exchanges must be Idempotent and Commutative – the Service Domains must handle duplicate exchanges and tolerate that
any business event may result in parallel threads of activity that can complete in different relative sequences based
on prevailing physical conditions
* Utilities and Middleware – to provide core Service Domain utilities such as a general service directory, data storage
and management, transaction logging, data analysis and reporting, transaction assurance and state/trigger handling
* Routing/Communication Capabilities – to be able to discover and establish all required Service Domain connections
with support for the associated message queue and event capabilities


# Compatibility with other formats
[ISO20022 and FTX](https://bian.org/about-bian/bian-and-other-standards-bodies/)

- ISO20022 - messaging
- FTX - messaging 


# Landscape
[v10](https://bian.org/servicelandscape-10-0-0/views.html)
[Guid](https://bian.org/wp-content/uploads/2020/10/BIAN-Semantic-API-Pactitioner-Guide-V8.1-FINAL.pdf)
