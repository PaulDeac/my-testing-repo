<p id="breadcrumb">

[Business Context](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemProviderQuery/BusinessContext) > Business Model

</p>



# Business Model

## Context

The OLIS FHIR Patient Query for Providers provides backend interface to the Health Care Provider  Applications and portals to allow a health care providers to view lab data for their patients in OLIS.


The health care provider application shall ensure that the required auditing information for the user is provided to the OLIS FHIR Patient Query for Providers interface to maintain traceability and comply with privacy and auditing requirements.

## Query Functionality

In order to comply with auditing and privacy requirements, the health care provider application should provide the following information with every request

• Hands at the keyboard

• Access Request Type

• HIC Organization responsible for enrolling the user

• Name of the Computer application being used by the user to access the data.



## The mandatory parameters for the query:

•	Patient Identifier

•	Gender 

•	Date of Birth

•	Start Date




## The optional parameters for the query:

•	Diagnostic Report Identifier

•	Test Request Code

•	Observation Code

•	Observation Status 

•	Abnormal Flag

•	End Date (this should default to either Observation Date or Last Updated Time in OLIS that the provider has chosen for the Start Date)


## Model

To meet this objective OLIS provides a Health Care Providerhealth care provider interface, built as a RESTful FHIR® interface, consumed by a variety of clients offering Health Care Providerhealth care provider applications to consume data ranging from traditional portals and EMRs to mobile apps and devices.


Figure 1 - Logical Model (Future State as Provider gateway will be built in the future).
 
  {{tree:ontariolaboratoriesi/model-duplicate-2/~overview}} 


## Supported Operations

The table below shows the allowed transaction for the DiagnosticReport with the corresponding HTTP operation.

**Table: Supported Operations**

| HTTP Operation | Interaction | Response Body Resource             |
|----------------|-------------|------------------------------------|
| Get            | Search      | Bundle containing DiagnosticReport |


