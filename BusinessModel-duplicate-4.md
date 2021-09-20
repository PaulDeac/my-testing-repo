<p id="breadcrumb">

[Business Context](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemConsumerQuery/BusinessContext) > Business Model

</p>


# Business Model

## Context
The OLIS Consumer Lab Reports Query provides backend interface to the Consumer Applications and portals to allow a consumer to view their lab data in OLIS. The query also allows authorized delegated user(s) to access the lab reports on behalf of the consumer. 

The Consumer Application shall be responsible for the onboarding, management, upkeep and maintenance of the users as well as the delegated user. The Consumer Application shall manage rules around access for a delegated user to view OLIS data on behalf of a consumer. This includes but not limited to rules around authenticating a user prior to submitting the query to OLIS as well as requirements around the ability of a delegated user to view OLIS data before the patient's ability to view the data themselves. 

The Consumer Application shall ensure that the required auditing information for the user is provided to the OLIS Consumer Query interface to maintain traceability and comply with privacy and auditing requirements. 



## Query Functionality

In order to comply with auditing and privacy requirements, the Consumer Application should provide the following information with every request

•             Hands at the keyboard

•             Access Request Type   

•             HIC Organization responsible for enrolling the user 

•             Name of the Consumer Application being used by the user to access the data.




## The mandatory parameters for the query:

•   Patient Identifier - Ontario health card number or medical record number

•   Patient Gender

•   Date of Birth

•	Start Date


## The optional parameters for the query:

•	Diagnostic Report Identifier

•	Test Request Code

•	Observation Code

•	Observation Status 

•	Abnormal Flag

•	End Date (this should default to either Observation Date or Last Updated Time in OLIS that the consumer has chosen for the Start Date)

## Model

To meet this objective OLIS provides a consumer interface, built as a RESTful FHIR® interface, consumed by a variety of clients offering consumers applications to consume data ranging from traditional portals and EMRs to mobile apps and devices.  

Figure 1 - Logical Model 


 {{tree:OntarioLaboratoriesI/OLISModel.png/~overview}} 

 ## Supported Operations

The table below shows the allowed transaction for the DiagnosticReport with the corresponding HTTP operation.

**Table: Supported Operations**

| HTTP Operation | Interaction | Response Body Resource             |
|----------------|-------------|------------------------------------|
| Get            | Search      | Bundle containing DiagnosticReport |
