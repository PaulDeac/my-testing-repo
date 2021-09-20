<p id="breadcrumb">

[Profiles & Operations](ProfilesOperations) > DiagnosticReport Search

</p>



# DiagnosticReport Search - OLIS FHIR Patient Query For Providers

DiagnosticReport search is simple RESTful interactions. It supports retrieving a lab results from OLIS for a provider by patient ID.

## Scope

This transaction involves a request by the following parameters:

**The mandatory parameters for the query:**
* Patient Identifier
* Gender 
* Date of Birth
* Start Date

**The optional parameters for the query:**

* Diagnostic Report Identifier
* Test Request Code
* Observation Code
* Observation Status 
* Interpretation (filter by abnormal results)
* End Date (this should default to either Observation Date or Last Updated Time in OLIS that the provider has chosen for the Start Date)


## Specification

The OLIS FHIR Patient Query For Providers is based on the HL7 STU3 Search operation.  

<br>


**Diagnostic Report Search Request**

The Diagnostic Report Search Request is an HTTP GET operation with multiple query parameters specified in Supported Search Parameters section below. The syntax of the request is 


`GET [base]/ DiagnosticReport?patient.identifier=[system]|[value]&patient.gender=[value]&patient.birthdate=[date]&issued=ge[date]`



**_Note: For the more details please reference to  Supported Search Parameters and Diagnostic Report Search Examples sections_**

<br>



**Diagnostic Report Search Response**

The relationship between the resources used in DiagnosticReport Search response is below: 


{{tree:ontariolaboratoriesi/olisfhirresources.png/~overview}}


* <a href="https://simplifier.net/ontariolaboratoriesi/diagnosticreport-provider" target="_blank">DiagnosticReport</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/procedurerequest-provider" target="_blank">ProcedureRequest</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/observation-provider" target="_blank">Observation</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/observationmicrobiologychild-provider" target="_blank">Observation(MicrobiologyChild)</a>


* <a href="https://simplifier.net/ontariolaboratoriesi/specimen-provider" target="_blank">Specimen</a>


* <a href="https://simplifier.net/ontariolaboratoriesi/patient-provider" target="_blank">Patient</a>


* <a href="https://simplifier.net/ontariolaboratoriesi/practitioner-provider" target="_blank">Practitioner(Ordering, Performing and Reporting)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/practitionercopied-provider" target="_blank">Practitioner(Copied to)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/practitionerattending-provider" target="_blank">Practitioner(Attending)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/practitioneradmitting-provider" target="_blank">Practitioner(Admitting)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationorderingfacility-provider" target="_blank">Organization(Ordering Facility)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationperforming-provider" target="_blank">Organization(Performing Laboratoty)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationreporting-provider" target="_blank">Organization(Reporting Laboratory)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationrequestplacer-provider" target="_blank">Organization(Test Request Placer)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationspecimencollector-provider" target="_blank">Organization(Specimen Collector)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationdestination-provider" target="_blank">Organization(Destination Laboratory)</a>


* <a href="https://simplifier.net/ontariolaboratoriesi/organizationassigner-provider" target="_blank">Organization(Identifier Assigner)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationrequesting-provider" target="_blank">Organization(Requesting)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/encounter-provider" target="_blank">Encounter</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/operationoutcome-provider" target="_blank">OperationOutcome</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/bundle-provider" target="_blank">Bundle</a>



## Extensions


* <a href="https://simplifier.net/OntarioLaboratoriesI/practitioner-copied/~overview" target="_blank">practitioner-copied</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organization-orderingfacility" target="_blank"> organization-orderingFacility</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organization-specimencollector" target="_blank"> organization-specimenCollector</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organization-testplacer" target="_blank"> organization-testPlacer </a>

* <a href="https://simplifier.net/ontariolaboratoriesi/report-replaceall" target="_blank"> report-replaceAll </a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organization-destinationlab" target="_blank"> organization-destinationLab </a>

* <a href="https://simplifier.net/ontariolaboratoriesi/en-qualifier" target="_blank">EN-qualifier</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/healthcard-versioncode" target="_blank"> healthCard-versionCode </a>

* <a href="https://simplifier.net/OntarioLaboratoriesI/data-subtype" target="_blank"> data-subtype </a>

* <a href="https://simplifier.net/ontariolaboratoriesi/request-eventtiming" target="_blank"> request-eventTiming </a>

* <a href="https://simplifier.net/ontariolaboratoriesi/specimen-numbersamplecontainer" target="_blank"> specimen-numberSampleContainer </a>

* <a href="https://simplifier.net/ontariolaboratoriesi/note" target="_blank"> note </a>

* <a href="https://simplifier.net/ontariolaboratoriesi/observation-sortkey" target="_blank"> observation-sortKey </a>

* <a href="https://simplifier.net/ontariolaboratoriesi/observation-subid" target="_blank"> observation-subID </a>

* <a href="https://simplifier.net/ontariolaboratoriesi/request-block" target="_blank"> request-block </a>

* <a href="https://simplifier.net/ontariolaboratoriesi/request-pointofcaretestid" target="_blank"> request-pointOfCareTestID </a>

* <a href="https://simplifier.net/ontariolaboratoriesi/requets-replace" target="_blank"> request-replace </a>

* <a href="https://simplifier.net/ontariolaboratoriesi/request-sortkey" target="_blank"> request-sortKey </a>

## Supported Search Parameters

<br>

**GET DiagnosticReport (query by Patient ID)**

Patient identifier parameter: **patient.identifier**

Only Ontario health card number is allowed as an identifier parameter in the current release.

* Example: `patient.identifier= [id-system-global-base]/ca-on-patient-hcn|12345678`

Patient Gender parameter: **patient.gender**

* Example: `patient.gender=male`

Patient Date of Birth parameter:  **patient.birthdate**

* Example: `patient.birthdate=1929-11-29`

Dates parameter: **issued**

* Example 1 : `issued=ge2016-01-02`

* Example 2: `issued=ge2015-02-25&issued=le2016-02-27`

Dates parameter: **specimen.collected**

* Example : `specimen.collected =ge2016-01-02`

Test Request code: **result.based-on:ProcedureRequest.code**

* Example: `result.based-on:ProcedureRequest.code= [code-system-local-base] /lab/test-request-codes|TR11663-2`

Interpretation parameter:**result.interpretation**

* Example 1: `result.intepretation=AB`
* Example 2: `result.intepretation=CR`

**Note:** This parameter allows the requestor to further restrict the search criteria to retrieve all abnormal results (AB) or critically abnormal only (CR).

Observation status: **result.status**

* Example: `result.status=final`

Observation code: **result.code**

* Example: `result.code= http://loinc.org|2028-9`

Diagnostic report identifier: **identifier**

* Example: `identifier= [id-system-local-base] /lab/report-id-lab-license-4004|543321`

Size limit (for response paging):**_count**

* Example:` _count=10`

If there is no _count in the search request, the server will return all matching records in one response.

<br>


Server will generate and return an additional parameter search-id as per Server Conformance section above.

* Example: `search-id= 017-11-16T20:37:03.0000000X128987`

<br>

Format: JSON (default) or XML

* Example: `format=[mime-type]:_format=application/fhir+json or _format=application/fhir+xml`

<br>

## Example

**Diagnostic Report Search Example**


`GET [base]/DiagnosticReport?patient.identifier=[id-system-global-base]/ca-on-patient-hcn|1008624486&patient.gender=male&patient.birthdate=1929-11-29&issued=ge2016-01-02 &_count=10`

<br>


In the returned header:

`[base]/DiagnosticReport?patient.identifier=[id-system-global-base]/ca-on-patient-hcn|1008624486&patient.gender=male&patient.birthdate=1929-11-29&issued=ge2016-01-02 &_count=10&search-id=017-11-16T20:37:03.0000000X128987`


**Examples of a search response can be found below**

| Resource | Example        |                                                                                      
---------------|-----------------------|
| DiagnosticReport          |  <a href="https://simplifier.net/ontariolaboratoriesi/diagnosticreport-example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/DiagnosticReport-example/~json" target="_blank"> JSON</a>                | 
| DiagnosticReport with Contained Resources        |  <a href="https://simplifier.net/ontariolaboratoriesi/diagnosticreport-example-contained" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/DiagnosticReport-example-contained/~json" target="_blank"> JSON</a>          |    
| ProcedureRequest         |  <a href="https://simplifier.net/ontariolaboratoriesi/procedurerequest-example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/ProcedureRequest-example/~json" target="_blank"> JSON</a>         |   
| Observation         |   <a href="https://simplifier.net/ontariolaboratoriesi/observation-example" target="_blank"> XML</a> / <a href="https://simplifier.net/ontariolaboratoriesi/observation-example/~json" target="_blank"> JSON</a>          |                        
| Observation(MicrobiologyChild)         | <a href="https://simplifier.net/ontariolaboratoriesi/observationmicrobiology-example" target="_blank"> XML</a> / <a href="https://simplifier.net/ontariolaboratoriesi/observationmicrobiology-example/~json" target="_blank"> JSON</a>          |                        
| Specimen        |  <a href="https://simplifier.net/OntarioLaboratoriesI/Specimen-example/~xml" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Specimen-example/~json" target="_blank"> JSON</a>          |   
| Patient         |   <a href="https://simplifier.net/ontariolaboratoriesi/patient-example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Patient-example/~json" target="_blank"> JSON</a>          |                      
| Practitioner(Ordering, Performing and Reporting Practitioner)         |   <a href="https://simplifier.net/OntarioLaboratoriesI/Practitioner-example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Practitioner-example/~json/~xml" target="_blank"> JSON</a>          |                        
| Practitioner(Copied to, Attending and Admitting Practitioner)         |  <a href="https://simplifier.net/ontariolaboratoriesi/practitioner-example-2/~xml" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Practitioner-example-2/~json" target="_blank"> JSON</a>          |                        
| Organization(Performing and Reporting Laboratory, Ordering Facility)        |  <a href="https://simplifier.net/ontariolaboratoriesi/organization-example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Organization-example/~json" target="_blank"> JSON</a>         |                        
| Organization(Destination Laboratory, Specimen Collector,Test Request Placer Organization and Requesting Organization)         |   <a href="https://simplifier.net/ontariolaboratoriesi/organization-example-2" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Organization-example-2/~json" target="_blank"> JSON</a>          |    
| Organization(Identifier Assigner)         |   <a href="https://simplifier.net/ontariolaboratoriesi/organization-example-3" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Organization-example-3/~json" target="_blank"> JSON</a></a>          |   
| Encounter         |   <a href="https://simplifier.net/ontariolaboratoriesi/encounter-example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Encounter-example/~json" target="_blank"> JSON</a>          |   
| OperationOutcome         |   <a href="https://simplifier.net/OntarioLaboratoriesI/OperationOutcome-example/~xml" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/OperationOutcome-example/~json" target="_blank"> JSON</a>          |     