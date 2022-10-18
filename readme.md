# Users (case study available):
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

# Technologically backed by:
- IBM https://www.ibm.com/support/pages/bian-mappings-ibm-banking-process-and-service-models
- Redhat https://www.redhat.com/en/resources/build-digital-foundation-coreless-banking-overview

# Size:
- 250+ Assets
- 19 Functional Patterns
- 17 Action Terms

# Structure:
BIAN Service Landscape consists of ~320 Service Domains. Grouped in Busiess Areas which in turn consist of Business Domains. A Service Domain is a conceptual functional design that can be mapped/related to a major application module.  Each service domain contains exactly 1 Asset. Combination of Asset and Functional Patter creates Control Record.

**Function Patters** can also be represented with 1-to-1 mapping to Generic Artifacts (just a  more tech terms) which can be mapped to Behaviour Qualifiers (even more concrete items).

> For example: Function Patter "Track" -> Generic Artifact "Log Record" -> Behaviour Qualifiers "Event"

Which are fine to devide in Qualifiers but they are out of BIAN scope.


**Action Term** Every Service Domain offers a collection of service operations and usually consumes or ‘delegates’ by calling the service operations of other Service Domains as needed to complete its work.  (Action Terms are like inteface methods, and BIAN provides mapping to REST specification)

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

> For example, the Service Domain Customer Relationship Management applies the ‘management’ control pattern to instances of a ‘customer relationship’ (an intangible asset) for the duration of their relationship with the bank and it does so for every bank customer.

# Implementation guidance

> Having both the dynamic (business scenario) and static (wireframe) models of the area of interest is useful to fully understand the service-centered design for the technical leads and architects.

[Addoption guide](https://view.ceros.com/hotwirepr/bian-guide-to-adoption/p/1)

## Mapping to REST

[APIs](https://bian.org/semantic-apis/)

To define BIAN Semantic APIs each default BIAN Service Domain service operation is matched to a ‘REST endpoint’ description. The scope/purpose of each individual BIAN Service Operation and its associated REST endpoint description is defined by three concerns:
* The Service Domain’s core functionality
* The service operation action term
* Optionally the Behavior Qualifier

There are several design properties that need to be reflected in the Service Domain specifications to support a fully
event driven design. Some example considerations are (in no specific order):
* Semantic Vocabulary Agreed to Required Precision – all exchanged semantic information must be defined as specific changes to the value of this information will often be a service triggering factor;
* State Management & Service Triggering – comprehensive event profiles for the Service Domains and their service triggering logic. This should include configuring thresholds and policies. These can be linked to key information attributes or with control record and control record partitions as defined by the behavior qualifier type;
* Service Operation Agreements and Policies – this includes more detailed service make-up definitions, including cross-referencing the policies and thresholds governing/triggering service exchanges as well as the required service performance, information integrity and security control features
* Transactional, Control, and Referential Exchanges – the required Service Domain information exchanges need to capture all transactional business activity, management command and control interactions and the background synchronization of shared reference information
* Defensive Operations – the Service Domain service operation implementation must always handle delayed/erroneous requests and respond in a graceful/defensive manner
* Exchanges must be Idempotent and Commutative – the Service Domains must handle duplicate exchanges and tolerate that any business event may result in parallel threads of activity that can complete in different relative sequences based on prevailing physical conditions
* Utilities and Middleware – to provide core Service Domain utilities such as a general service directory, data storage and management, transaction logging, data analysis and reporting, transaction assurance and state/trigger handling
* Routing/Communication Capabilities – to be able to discover and establish all required Service Domain connections with support for the associated message queue and event capabilities


# Implementation Approache

BIAN follows component based design in contrast to process based design.

## Contrasting the Potentially Conflicting Issues of Performance and Consistency

The component based and process information architectures both have specific strengths and weaknesses. Many of these may be leveraged or mitigated with different application design and implementation techniques. At the conceptual level the differentiating properties are:

### Strengths
| Component Information Architecture  | Process Information Architecture |
|--------------------------------------|----------------------------------|
| all business information governance is uniquely assignable to a single responsible business entity | business information is defined to support the processing logic precisely
| the business context for information is well defined. Avoiding the incorrect inference that similar types of information used in different business situations must always share the same information value | business information can be structured to ensure highly efficient access throughout the process |
| the complete life-cycle of the information can be managed, ensuring appropriate action can be taken to maintain the integrity and currency of the information throughout its usage |common enterprise reference business information can be easily duplicated and integrated where available |

### Weaknesses
| Component Information Architecture  | Process Information Architecture |
|--------------------------------------|----------------------------------|
|providing access to singularly governed information introduces the potential for delay/latency and possible access limitations/constraints (during information updates in particular). | local business information views fragment the overall enterprise model and can lead to extensive processing and data inconsistencies |
| | designs may not be readily adaptive to changes and enhancements |

## Disclaimer

### Values:
key insights the solution designer should take from the conceptual Service Domains as they set out the overall structure of their application design include:
* The core business role/function supported by each Service Domain partition
* The type of business information the Service Domain governs
* Representative service operations offered as major application partition interfaces
* From associated scenarios and wireframes an indication of any delegated service dependencies# Landscape

### Limitations
As stated, at the conceptual level solution architects/designers should be aware that the BIAN requirement descriptions are limited:
* They only describe general/mainstream requirements,
* They do not address errors and exception conditions
* They do not consider any non-functional properties such as performance and security

### Properties

Components define business functional building blocks, each representing the capacity to perform a specific business need. **Operational reuse** is not to be confused with the more conventional code-based **utility re-use** – where similar processing logic can be encoded and re-used.

The key difference is that though the SW utility functions as an autonomous capability, it does not represent a uniquely assignable business responsibility. By definition there can be many concurrent instances of a SW utility operating completely independently. The utility implementation ensures that the logic is applied consistently and improves software integrity and development productivity but it does not specifically address the operational re-use of a discrete business capability. Not surprisingly a SW Utility will typically be much finer grained than a Service Domain.

The component design adopted by BIAN has a number of implications for a Service Domain’s information management:
* **Persistence** – the BIAN Service Domain defines a persistent business capability with its associated information store (database) – it may be active or inactive at any point in time, but it can always be available to respond to external service requests and typically also executes its own internal schedule of actions
* **Fully Encapsulated/Autonomous** – because the Service Domain is responsible for the complete life cycle operation of its business role it consequently governs all of the associated business logic and information required to perform its responsibilities for its complete lifespan.
* **Discrete/Non-overlapping** – each Service Domain is defined to perform a single discrete and unique business function.  It may delegate actions through service calls to other specialized Service Domains. But the Service Domain is accountable for the outcome of all delegated tasks and the interpretation of any returned information.

As a result of these design properties all enterprise business information can be **uniquely assigned to a single governing Service Domain** where it is maintained for its complete lifespan. The information exchanged through service operations provides the values/status details of information governed by one Service Domain that can be interpreted and applied to information governed by another. But each Service Domain maintains its own complete and independent information viewpoint and is responsible for the integrity of its own governed information.

### Service Domain Externalization

Revisiting the externalization decisions underlying a Service Domain can be useful for technical leads and architects to better understand its business role and can also help when mapping Service Domain partitions to legacy applications. Determining whether a function or associated business information is contained within a Service Domain or should be ‘externalized’ and accessed through a service boundary boils down to a single test:

> Is it (the considered function or information) sensibly considered a feature of or property of the Service Domain’s control record instance, and can it only meaningfully exist as an aspect of that control record and its life cycle? Or does it refer to some other distinct entity with its own independent life cycle, that is governed by its own specialized Service Domain and handled as a property or feature of its control records?

### Organization Configuration of Service Domain
To support organizational configuration a Service Domain may be deployed in four different implementation forms:
* As a local proxy that provides access to a shared centralized service
* As the central service supporting multiple proxies
* As the local fulfillment capability but with reporting obligations to a coordinating ‘parent’
* As the central consolidation and coordination ‘parent’ capability

### Service Domain Roles

* **Core** – the Service Domain instance running in the application is the single, master version for the enterprise. It is the only physical instance and the sole source for its services and information
* **Proxy** – the Service Domain running in the application supports all local requirements but is connected to an external ‘master’ Service Domain (that will be running as a ‘Core’ Service Domain in some other application)
* **Utility** – is a local/proxy implementation of a Service Domain where due to its specific business role, it can operate with no or limited need to connect and synchronize with a master/core version
* **External** – records that there is a direct connection from the application cluster to the Service Domain to either offer and/or subscribe to services. These define the main external application interfaces
* **Peripheral** – Sometimes it helps to include additional Service Domains in the cluster diagram that have some indirect involvement (through an External Service Domain) simply to clarify limitations in the external application boundary

# Implementation Suggestions

## Legacy Wrapping

### Externalization applied to legacy application modules
The approach to develop the target state component model for the wrapped legacy application includes these main steps:
1. Working through the functional scope of the legacy application and referencing the Service Domains and their associated control record specifications, identify mapped Service Domains
2. The layout of an Application Cluster diagram is then initiated to represent the target state/boundary for the wrapped legacy application.
3. The application cluster diagram is populated as key decisions are made as to whether mapped Service Domain component functionality should remain within the application cluster or be externalized.
4. For Service Domain mapped functionality that is to remain within the wrapped application a further decision must be made as to whether it is to represent the core or a proxy instance of this functionality for the enterprise.
5. For all other mapped functionality, the associated Service Domain capabilities should eventually be sourced externally from alternate applications.
6. Finally, for key external interfaces to the legacy application, the existing interfaced system should also be mapped to Service Domains to ensure there is no redundancy/overlap with the target application Service Domain component make-up

### Reconciling master/slave information governance

The governed information inventory can be related to the current legacy application database/information and categorized as follows:
* It represents Master data that is governed by the application – and so must provide external access as necessary
* It represents Proxy Master data that is governed in another instance of the Service Domain in some other application. Reconciliation services need to be established to synchronize with this external source
* Is a local copy of externally governed information – i.e. should be retrieved through an external interface/service call and the values interpreted and applied to the internal business information model as appropriate

### Wrapping & service enablement

The types of mitigating logic that can be built into the container architecture include:
* Functional extensions – adding ‘front-end’ functionality and supporting operating requirements that can’t be easily built into the legacy codebase
* Synchronization – capabilities to handle the master/slave data synchronization requirements between systems
* Proxy capabilities – support temporary functions that will eventually be provided by alternate/external service providers
* Session optimization and data caching – the wrapper may streamline access management and can also include logic that performs advanced probabilistic data look-up and caching to reduce host access costs and latency

### Migration strategies – the parallel core configuration
Bigbang vs Parallel Core vs Incremental vs ...

## General Approaches (for both Green Field and Legacy Wrapping)
### Shared Platform to Eliminate Service Exchanges
In this approach the two Service Domain’s maintain their own logical information perspectives, but the exchanged information attributes are mapped to common physical storage. Data management and access controls are required to manage concurrent access but updates made by one Service Domain are instantly visible to the other. The information is logically exchanged, but no actual physical data transfer takes place.
### Shared Platform to Support Consolidated Cross-Service Domain Reporting
In this situation one Service Domain is responsible for the consolidation, analysis and reporting on information obtained from potentially multiple source Service Domains.

### BIAN Type 1,2 & 3 external access governance patterns
1. Direct to Core – the external access is governed by a gateway that implements basic customer authentication. The gateway then connects directly to the host system. In many situations re-using an existing external interface that might have been implemented to support web based or contact center servicing
2. Wrapped Host – in addition to the access gateway, the wrapped host approach includes a front end capability that can address shortfalls in the host systems.  This can support host migration and repurposing efforts. It includes coordinating access with multiple systems for more complex transaction, resolving master slave data conflicts, host access session optimization, information advanced look-up and caching and supporting functional extensions
3. Component Architecture – involves a comprehensive set of controls to manage external access to allow direct connection to the internal capabilities of the bank.  A wireframe of the external access platform is shown below



[v10](https://bian.org/servicelandscape-10-0-0/views.html)
[Guide](https://bian.org/wp-content/uploads/2020/10/BIAN-Semantic-API-Pactitioner-Guide-V8.1-FINAL.pdf)


# Compatibility with other formats
[ISO20022 and FTX](https://bian.org/about-bian/bian-and-other-standards-bodies/)

- ISO20022 - messaging
- FTX - messaging 
