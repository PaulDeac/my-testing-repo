<p id="breadcrumb">

[Business Context](BusinessContext) > Business Model

</p>

# Business Model

## Context

This specification supports two business models of OLIS FHIR queries:

- The OLIS FHIR Patient Query for Providers provides backend interface to the Health Care Provider  Applications and portals to allow a health care providers to view lab data for their patients in OLIS.

- The OLIS FHIR COVID Query for Public Health Units (PHUs) provides backend interface to the public health applications to allow them to view COVID specific results from OLIS.

In both models, the requesting applications shall ensure that the required auditing information for the user is provided to the interface to maintain traceability and comply with privacy and auditing requirements.

## Query Functionality

In order to comply with auditing and privacy requirements, the requesting application should provide the following information with every request

• Hands at the keyboard

• Access Request Type

• HIC Organization responsible for enrolling the user

• Name of the Computer application being used by the user to access the data.


## Mandatory Parameters

### The mandatory parameters for OLIS FHIR Patient Query For Providers:

•	Patient Identifier

•	Gender 

•	Date of Birth

•	Start Date


### The mandatory parameters for OLIS FHIR COVID query:

•	Start Date

In addition, the correct scope value must be provided to ensure only COVID results will be returned. This is specified in the OAuth token specified in [Connectivity](Connectivity) page.

## Optional Parameters

### The optional parameters for OLIS FHIR Patient Query For Providers:

•	Diagnostic Report Identifier

•	Test Request Code

•	Observation Code

•	Observation Status 

•	Abnormal Flag

•	End Date (this should default to either Observation Date or Last Updated Time in OLIS that the provider has chosen for the Start Date)

### The optional parameters for OLIS FHIR COVID query:

• _count - this indicates the maximum number of records that should be returned. If this is not provided, all records will be returned.

## Model

To meet this objective OLIS provides a provider query interface, built as a RESTful FHIR® interface, consumed by a variety of clients offering to consume data ranging from traditional portals and EMRs to mobile apps and devices.


Figure 1 - Logical Model (Future State as Provider gateway will be built in the future).
 
  {{tree:ontariolaboratoriesi/model-duplicate-2/~overview}} 


## Supported Operations

The table below shows the allowed transaction for the DiagnosticReport with the corresponding HTTP operation.

**Table: Supported Operations**

| HTTP Operation | Interaction | Response Body Resource             |
|----------------|-------------|------------------------------------|
| Get            | Search      | Bundle containing DiagnosticReport  |


