<p id="breadcrumb">

[Profiles & Operations](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemConsumerQuery/ProfilesOperations) > Diagnostic Report Search

</p>


## Diagnostic Report Search

DiagnosticReport search is simple RESTful interactions. It supports retrieving a lab results from OLIS for a consumer by patient ID.

### Scope

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
* Abnormal Flag
* End Date (this should default to either Observation Date or Last Updated Time in OLIS that the consumer has chosen for the Start Date)

### Ontario Laboratory FHIR® Resources

{{tree:ontariolaboratoriesi/olisfhirresources.png/~overview}}

### Specification

The FHIR OLIS Consumer Query specification is based on the HL7 STU3 Search operation.  

**Diagnostic Report Search Request**

The Diagnostic Report Search Request is an HTTP GET operation with multiple query parameters specified in Supported Search Parameters section below. The syntax of the request is 

*GET [base]/ DiagnosticReport?patient.identifier=[system]|[value]&patient.gender=[value]&patient.birthdate=[date]&issued=ge[date]*

**_Note: For the more details please reference to  Supported Search Parameters and Diagnostic Report Search Examples sections_**

**Diagnostic Report Search Response**


* <a href="https://simplifier.net/ontariolaboratoriesi/diagnosticreport" target="_blank">Diagnostic Report</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/procedurerequest" target="_blank">Procedure Request</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/observation" target="_blank">Observation</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/observationmicrochild" target="_blank">Observation (Microbiology)</a>


* <a href="https://simplifier.net/ontariolaboratoriesi/specimen" target="_blank">Specimen</a>


* <a href="https://simplifier.net/OntarioLaboratoriesI/Patient/~overview" target="_blank">Patient</a>


* <a href="https://simplifier.net/ontariolaboratoriesi/practitionerordering" target="_blank">Practitioner (Ordering)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/practitionercopied" target="_blank">Practitioner (Copied to)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/practitionerattending" target="_blank">Practitioner (Attending)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/practitioneradmitting" target="_blank">Practitioner (Admitting)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationorderingfacility" target="_blank">Organization (Ordering Facility)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationperforming" target="_blank">Organization (Performing Laboratoty)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationreporting" target="_blank">Organization (Reporting Laboratory)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationrequestplacer" target="_blank">Organization (Test Request Placer)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationspecimencollectorcenter" target="_blank">Organization (Specimen Collector Center)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationdestination" target="_blank">Organization (Destination Laboratory)</a>


* <a href="https://simplifier.net/ontariolaboratoriesi/organizationassigner" target="_blank">Organization (Identifier Assigner)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/encounter" target="_blank">Encounter</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/operationoutcome" target="_blank">Operation Outcome</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/bundle" target="_blank">Bundle</a>



### Extensions


* <a href="https://simplifier.net/ontariolaboratoriesi/extensioncopiedpractitioner" target="_blank"> lab-ext-cc-list (Copied Practitioner)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensionorderingfacility" target="_blank"> lab-ext-ordering-facility (Ordering Facility)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensionspecimencollectorcenter" target="_blank"> lab-ext-scc (Specimen Collector Center)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensiontestrequestplacer" target="_blank"> lab-ext-trq-placer (Test Request Placer)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensionreplaceall" target="_blank"> lab-ext-replace-all (Replace All)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensiondestinationlab" target="_blank"> lab-ext-dest-lab (Destination Laboratory)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/en-qualifier" target="_blank"> en-qualifier (EN-Qaulifier)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensionversioncode" target="_blank"> ext-id-health-card-version-code (Health Card Version Code)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensiondatasubtype" target="_blank"> lab-ext-subtype (Data Subtype)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensioneventtiming" target="_blank"> observation-eventTiming (Event Timing)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensionnambersamplecontainer" target="_blank"> lab-ext-container-sample-num (Number of Sample Containers)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensionnote" target="_blank"> lab-ext-note (Notes)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensionobservationsortkey" target="_blank"> lab-ext-obs-sort-key (Observation Sort Key)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensionobservationsubid" target="_blank"> lab-ext-obs-sub-id (Observation Sub ID)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensionrecordblock" target="_blank"> lab-ext-record-block (Test Request Blocking Indicator)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensionpointofcaretestid" target="_blank"> lab-ext-poc-test-id (Point-of-care Test Identifier)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensionrecordreplace" target="_blank"> lab-ext-record-replace (Test Request Replace Amend)</a>
* <a href="https://simplifier.net/ontariolaboratoriesi/extensiontestrequestsortkey" target="_blank"> lab-ext-trq-sort-key (Test Request Sort Key)</a>

### Supported Search Parameters

<br>

**GET DiagnosticReport (query by Patient ID)**

Patient identifier parameter: **patient.identifier**

Only Ontario health card number is allowed as an identifier parameter in the current release.

* Example: patient.identifier= [id-system-global-base]/ca-on-patient-hcn|12345678

Patient Gender parameter: **patient.gender**

* Example: patient.gender=male

Patient Date of Birth parameter:  **patient.birthdate**

* Example: patient.birthdate=1929-11-29

Dates parameter: **issued**

* Example 1 : issued=ge2016-01-02

* Example 2: issued=ge2015-02-25&issued=le2016-02-27

Dates parameter: **specimen.collected**

* Example : specimen.collected =ge2016-01-02

Test Request code: **result.based-on:ProcedureRequest.code**

* Example: result.based-on:ProcedureRequest.code= [code-system-local-base] /lab/test-request-codes|TR11663-2

Interpretation parameter:**result. interpretation**

* Example: result.interpretation=AB

Observation status: **result.status**

* Example: result.status=final

Observation code: **result.code**

* Example: result.code= http://loinc.org|2028-9

Diagnostic report identifier: **identifier**

* Example: identifier= [id-system-local-base] /lab/report-id-lab-license-4004|543321

Size limit (for response paging):**_count**

* Example: _count=10

If there is no _count in the search request, the server will return all matching records in one response.

<br>


Server will generate and return an additional parameter search-id as per Server Conformance section above.

* Example: search-id= 017-11-16T20:37:03.0000000X128987

<br>

Format: JSON (default) or XML

* Example: format=[mime-type]:_format=application/fhir+json or _format=application/fhir+xml

<br>

### Example

**Diagnostic Report Search Example**

<br>

GET [base]/ DiagnosticReport?patient.identifier=[id-system-global-base]/ca-on-patient-hcn| 1008624486&patinet.gender=male&patient.birthdate=1929-11-29&issued=ge2016-01-02 &_count=10

<br>

In the returned header: [base]/ DiagnosticReport? patient.identifier=[id-system-global-base]/ca-on-patient-hcn|1008624486& patient.gender=male&patinet.birthdate=1929-11-29&issued=ge2016-01-02 &_count=10&search-id=017-11-16T20:37:03.0000000X128987

**Examples of a search response can be found below**

| Resource | Example        |                                                                                      
---------------|-----------------------|
| Diagnostic Report          |  <a href="https://simplifier.net/ontariolaboratoriesi/diagnosticreport-example-duplicate-3" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/DiagnosticReport-example-duplicate-3/~json" target="_blank"> JSON</a>                | 
| Diagnostic Report with Contained Resources        |  <a href="https://simplifier.net/ontariolaboratoriesi/diagnosticreport-example-duplicate-2" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/DiagnosticReport-example-duplicate-2/~json" target="_blank"> JSON</a>          |    
| Procedure Request         |  <a href="https://simplifier.net/ontariolaboratoriesi/procedurerequest-example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/ProcedureRequest-example/~json" target="_blank"> JSON</a>         |   
| Observation         |   <a href="https://simplifier.net/ontariolaboratoriesi/observation-example-duplicate-3" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Observation-example-duplicate-3/~json" target="_blank"> JSON</a>          |                        
| Observation Microbiology         | <a href="https://simplifier.net/ontariolaboratoriesi/observation-example-duplicate-2" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Observation-example-duplicate-2/~json" target="_blank"> JSON</a>          |                        
| Specimen        |  <a href="https://simplifier.net/OntarioLaboratoriesI/Specimen-example/~xml" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Specimen-example/~json" target="_blank"> JSON</a>          |   
| Patient         |   <a href="https://simplifier.net/ontariolaboratoriesi/patient-example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Patient-example/~json" target="_blank"> JSON</a>          |                      
| Practitioner (Ordering)         |   <a href="https://simplifier.net/OntarioLaboratoriesI/Practitioner-example-duplicate-2/~xml" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Practitioner-example-duplicate-2/~json/~xml" target="_blank"> JSON</a>          |                        
| Practitioner (Copied to, Attending and Admitting Practitioner)         |  <a href="https://simplifier.net/ontariolaboratoriesi/practitioner-example-duplicate-3/~xml" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Practitioner-example-duplicate-3/~json" target="_blank"> JSON</a>          |                        
| Organization (Performing and Reporting Laboratory, Ordering Facility)        |  <a href="https://simplifier.net/ontariolaboratoriesi/organization-example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Organization-example/~json" target="_blank"> JSON</a>         |                        
| Organization (Destination Laboratory, Specimen Collector Center and Test Request Placer Organization)         |   <a href="https://simplifier.net/ontariolaboratoriesi/organization-example-duplicate-2" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Organization-example-duplicate-2/~json" target="_blank"> JSON</a>          |    
| Organization (Identifier Assigner)         |   <a href="https://simplifier.net/ontariolaboratoriesi/organization-example-duplicate-3" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Organization-example-duplicate-3/~json" target="_blank"> JSON</a></a>          |   
| Encounter         |   <a href="https://simplifier.net/ontariolaboratoriesi/encounter-example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Encounter-example/~json" target="_blank"> JSON</a>          |   
| Operation Outcome         |   <a href="https://simplifier.net/OntarioLaboratoriesI/OperationOutcome-example/~xml" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/OperationOutcome-example/~json" target="_blank"> JSON</a>          |                       
                    
