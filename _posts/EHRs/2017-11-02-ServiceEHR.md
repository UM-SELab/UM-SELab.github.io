---
layout: post
title:  "Service-oriented EHR Sharing System"
date:   2017-11-03 
categories: EHRs 
author: Nafees Qamar, Yilong Yang, Andras Nadas, Zhiming Liu and Janos Sztipanovits
---

Privacy-Preserving EHR Sharing System takes on the problem of automatically identifying clinically-relevant patterns in medical datasets without compromising patient privacy. To achieve this goal, we treat datasets as a black box for both internal and external users of data that lets us handle clinical data queries directly and far more e ciently. The novelty of the approach lies in avoiding the data de-identification process often used as a means of preserving patient privacy. The implemented toolkit combines software engineering technologies such as Java EE and RESTful web services, to allow exchanging medical data in an unidentifiable XML format as well as restricting users to the need-to-know principle. Our technique also inhibits retrospective processing of data, such as attacks by an adversary on a medical dataset using advanced computational methods to reveal Protected Health Information (PHI). The approach is validated on an endoscopic reporting application based on openEHR and MST standards. From the usability perspective, the approach can be used to query datasets by clinical researchers, governmental or non-governmental organizations in monitoring health care services to improve quality of care.

{% include img.html url="new_diagram.png" %}

Patients’ Electronic Health Records (EHRs) are stored, processed, and transmitted across several healthcare platforms and among clinical researchers for on-line diagnostic services and other clinical research. This data dissemina- tion serves as a basis for prevention and diagnosis of a disease and other secondary purposes such as health system planning, public health surveillance, and generation of anonymized data for testing. However, exchanging data across organizations is a non-trivial task because of the embodied potential for privacy intrusion. Medical organizations tend to have confidential agreements with patients, which strictly forbid them to disclose any identifiable information of the patients. Health Insurance Portability and Accountability Act (HIPAA) explicitly states the confidentiality protection on health information that any sharable EHRs system must legally comply with. To abide by these strict regulations,data custodians generally use de-identification1 techniques so that any identifiable information on patient’s EHR can be suppressed or generalized. 

However, in reality, research indicates that 87% of the population of U.S. can be distinguished by sex, date of birth and zip code. We can define quasi-identifiers as the background information about one or more people in the dataset. If an adversary has knowledge of these quasi-identifiers, it can possibly recognize an individual and take advantage of his clinical data. On the other hand, we can find out most of these quasi-identifiers have statistical meanings in clinical research. There exists a paradox between reducing the likelihood of disclosure risk and retaining the data quality. For instance, if information related to patients’ residence was excluded from the EHR, it would disable related clinical partners to catch the spread of a disease. Thus, strictly filtered data may lead to failure in operations. Conversely, releasing data including patients’ entire information including residence, sex and date of birth would bring a higher disclosure risk. 

we address the emerging problem of de-identification techniques, namely, the problem of offering de-identified dataset for a secondary purpose that makes it possible for a prospective user to perform retrospective processing of medical data endangering patient privacy. Figure  overviews the proposed technique, and the standard data request process. Our approach differs from the traditional techniques in the sense that it employs software engineering principles to isolate and develop key requirements of data custodians and requesters. We apply Service-Oriented Architecture (SOA) that provides an effective solution for connecting business functions across the web-both between and within enterprises.

### Data Structure

{% include img.html url="datastructure.png" %}

Figure 2 describes the data structure of the GastrOS database. GastrOS database contains the following tables: the clinicaldetection (doctor detection records), patient (patient information), and examination (examination records) tables are stored in the database.
    
The patient table has two relations: one patient may have more than one clinical detection record or examination record by doctor(s), so the patient id is added as a foreign key in tables ClinicalDection and Examination. GastrOS is a toy database example with insu cient amount of data available. The original database contains less than 20 rows in each table that makes is not useful for our SQL queries. Therefore, we automatically generated virtual data of 10,000 entries (note that any real data on patients also cannot be published.)

{% include img.html url="rbac.png" %}

### Organization Login
Our prototype system implements role-based access control, effectively employed in our previous works. For example, for a medical dataset, operations might include insert, delete, append, and update. The data model of RBAC is based on five data types: users, roles, objects, permissions and executable operations by users on objects.

A sixth data type, session, is used to associate roles temporarily to users.A role is considered a permanent position in an organization whereas a given user can be switched with another user for that role. Thus, rights are offered to roles instead of users. Roles are assigned to permissions that can later be exercised by users playing these roles. Modeled objects in RBAC are potential resources to protect. Operations are viewed as application-specific user functions. UA is user assignment and PA is permission assignment. For example, Figure shows a list of queries provided to an organization role.

{% include img.html url="organA.png" %}

### Enabling dynamic clinical queries
The construction and execution of clinical queries on a given dataset are implemented through a web-interface of the tool. The interface allows a user to dynamically construct a clinical query on a dataset. Thus, it adds a greater flexibility to the query mechanism in developing user-oriented analysis of a dataset. For instance, Figure demonstrates how to execute a query such as "Total number of dialysis endoscopic examination of a country starting and ending on a particular date, respectively."

{% include img.html url="dynamicQ.png" %}

### Query Result:
These queries show that all specific details on patients are avoided when executing a query, which also means that it disables all direct accesses to patient records. It is actually realized by providing a more aggregated form of data on patients instead of conventional techniques that provide medial datasets to infer such details. Note that the toolkit does not allow any query that provides specific information on patients, such as "Provide details of all patients with a certain age". These queries are directly irrelevant to researchers since they are mainly interested in collective analysis on a dataset. The idea of combining web services with SQL queries is although not new, but it tends to provide a technological solution to a technological problem avoiding medical data re-identification risks. The rationale Using Java EE stems from the fact that it provides an easy way to develop applications, for example, EJB are convenient to use by adding only one annotation. Java EE is also widespread being largely used both in academia and industry.

{% include img.html url="dqueryresult.png" %}

### Publication

[Nafees Qamar, Yilong Yang, Andras Nadas, Zhiming Liu and Janos Sztipanovits. Anonymously Analyzing Clinical Datasets. ITCH 2016](/assets/publication/icth2016.pdf)

### Tutorial Demo
{% include video.html url="ServiceEHR.mp4" %}
