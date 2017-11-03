---
layout: post
title:  "Distributed EHR Sharing System"
date:   2017-11-03 
categories: EHRs 
author: Yilong Yang, Xiaoshan Li, Nafees Qamar, Wei Ke, Peng Liu, and Zhiming Liu
---
Legacy Electronic Health Records (EHRs) systems were not developed with the level of connectivity expected from them nowadays. Therefore, interoper- ability weakness inherent in the legacy systems can result in poor patient care and waste of financial resources. Large hospitals are less likely to share their data with external hospitals due to economic and political reasons. Motivated by these facts, we aim to provide a set of software implementation guidelines, i.e., MedShare to deal with interoperability issues among disconnected healthcare systems.

{% include img.html url="distributeEHRoverview.png" %}

#### Methods
We propose an integrated architecture which is implemented using: 1) a data extractor to fetch legacy medical data from a hemodialysis center, 2) convert- ing it to a common data model, 3) indexing patient information using the Hashmap technique, and 4) a set of services and tools that can be installed as a coherent en- vironment on top of stand-alone EHRs systems. Our distributed resource sharing system is implemented by using lightweight JavaEE Framework Spring, NodeJS and JWT.

#### External view
The Figure 6 illustrates the external view of our system. Legacy EHR systems provide the services of data conversion to convert shared EHRs from a legacy system to a distributed EHR system. However, using the authentication service the doctor and the patient are authorized. By using both services from the local legacy systems, the unified EHR sharing system provides two services: 1) It allows to run a query on the MedShare. 2) The audit service handles the privacy requirements of the system and post- breach data analysis, which is not detailed in this paper.

{% include img.html url="DEHRarch1.png" %}

#### Internal view
The internal view of the unified EHR sharing system Figure 7 shows how the sub-systems collaborate to provide the required medical data querying mechanism from the di↵erent hospitals. The subsystems use the services provided by the index system in the data center to locate EHRs, then using the service of transfer EHRs in each subsystem to transfer all requested EHRs. To understand what is a service in the system, readers are directed to the implementation section of the paper.

{% include img.html url="DEHRarch2.png" %}


#### Results
Our work enabled three cooperating but autonomous hospitals to mutually exchange medical data and helped them develop a common reference architecture. It lets stakeholders retain control over their patient data, winning the trust and confi- dence much needed towards a successful deployment of MedShare. Security concerns were e↵ectively addressed that also included patient consent in the data exchange pro- cess. Thereby, the implemented toolset o↵ered a collaborative environment to share EHRs by the healthcare providers.

#### System Prototyping and Demonstration

{% include img.html url="DEHRimplementation.png" %}

`Data Infrastructure Layer` The data infrastructure, as shown in Figure 5, shows the data storage based on MongoDB [1] which is NoSQL database, more precisely a non- relational database. To deal with the complexity of medical data, it requires to have an adaptable format facilitating the data transformations easily across multiple sources. This approach overcomes the bottlenecks of traditional databases. Using MongoDB also helps mutability and scalability features of EHRs.

`Technical Framework Layer` All the components described in our presented archi- tectural models are implemented by the lightweight Java EE framework Spring [6]. The required two-way authentication service in the legacy EHR system is implemented as a RESTFul web service by NodeJS [31] and JSON Web Token (JWT) [10]. A RESTFul service can be defined as a means to hold query parameters. Contrary to JavaEE, N- odeJS has the advantage of utilizing low resources to support high concurrency, which is good at scaling it to industrial problems. While JWT is a compact, URL-safe approach for representing claims between two communicating ends. JWT provides foundational authentication service to RESTFul web services. Those two techniques guarantee the reliability and safety of the authentication process.

`Discovery and Information Exchange Services Layer` This layer has two Spring MVC services and a web service for authentication. The Locate Service, which is im- plemented using Spring MVC framework, identifies the required EHR location from the patients indexed in the MongoDB data infrastructure. The Locate Service locates the EHRs based on the search conditions and transmits it to the doctor. The Data Access is technically similar to Locate Service but functions di↵erently. It retrieves relevant patient data from the identified source. The Authentication Service provides the authorization service to the patient when the doctor requests for a specific EHR. The authentication also requires a service that integrates legacy EHR system into the authentication process. The synchronization service timely triggers the replication of the shared EHRs and updates the indexes in the patient indexing server. The audit service provides the log and tracking services to avoid data breach and trace irregularities. The authentication component is deployed in all the hospitals. The EHR query component is deployed in all the hospitals to provide the data transmission service, and in the patient indexing server to provide the locating service. The synchronization service is deployed in all the hospitals and the data center to replicate shared EHRs and update indexes. The audit service is deployed on all computers because logs are generated and stored in the patient indexing server and all the other hospitals.

`Front-end Medical Resource Sharing Layer` This layer combines all the described layers and directly utilizes the services available in the discovery and information exchange services layer. Through this front-end the end user poses a query to the shared EHRs resources and retrieves a list of resources against the targeted EHR. The Audit service holds the system users accountable for their action in the system. More precisely, the doctor can distributively retrieve all the relevant records of the patient among all the hospitals while preserving patient privacy.

#### Conclusion
HL7 is currently the most widely used industry standard, however, legacy EHR systems especially in developing countries encounter many political and economical issues before they could embrace open standards. Fear of losing patients predominantly exists in healthcare providers; therefore, we suggest a gradual replace- ment of the legacy EHRs systems without asking healthcare providers to replace their working and entrusted systems.