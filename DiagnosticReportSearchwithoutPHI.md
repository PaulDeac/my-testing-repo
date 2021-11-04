<p id="breadcrumb">

[Profiles & Operations](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemConsumerQuery/ProfilesOperations) > Diagnostic Report Search without PHI

</p>

# DiagnosticReport Search without PHI

DiagnosticReport search without PHI is simple RESTful interaction leveraging the privacy-preserving interface. It supports retrieving a lab results from OLIS for a consumer without specifying patient identifier or demographics.

## Scope

This transaction involves a request by the following parameters:

**The mandatory parameters for the query:**
* Start Date

**The optional parameters for the query:**

* Diagnostic Report Identifier
* Test Request Code
* Observation Code
* Observation Status 
* Interpretation (filter by abnormal results)
* End Date (this should default to either Observation Date or Last Updated Time in OLIS that the consumer has chosen for the Start Date)

## Interaction Diagram

The following diagram illustrates the high level flow for a PHI-less lab request to OLIS backend.

{{tree:ontariolaboratoriesi/fpx-flow}}

## Specification

The FHIR OLIS Consumer Query specification is based on the HL7 STU3 Search operation.  

**DiagnosticReport Search Request**

The DiagnosticReport Search Request is an HTTP GET operation with one mandatory query parameter and other optional parameters specified in Supported Search Parameters section below. The syntax of the request is

`GET [base]/DiagnosticReport?issued=ge[date]`

**_Note: For the more details please reference to  Supported Search Parameters and DiagnosticReport Search Examples sections_**

<br>
<br>

**DiagnosticReport Search Response**

The relationship between the resources used in DiagnosticReport Search response is below: 

{{tree:ontariolaboratoriesi/olisfhirresources.png/~overview}}

<br>


* <a href="https://simplifier.net/ontariolaboratoriesi/diagnosticreport" target="_blank">DiagnosticReport</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/procedurerequest" target="_blank">ProcedureRequest</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/observation" target="_blank">Observation</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/observationmicrobiologychild" target="_blank">Observation(MicrobiologyChild)</a>


* <a href="https://simplifier.net/ontariolaboratoriesi/specimen" target="_blank">Specimen</a>


* <a href="https://simplifier.net/OntarioLaboratoriesI/Patient/~overview" target="_blank">Patient</a>


* <a href="https://simplifier.net/ontariolaboratoriesi/practitioner" target="_blank">Practitioner(Ordering, Performing and Reporting)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/practitionercopied" target="_blank">Practitioner(Copied to)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/practitionerattending" target="_blank">Practitioner(Attending)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/practitioneradmitting" target="_blank">Practitioner(Admitting)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationorderingfacility" target="_blank">Organization(Ordering Facility)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationperforming" target="_blank">Organization(Performing Laboratory)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationreporting" target="_blank">Organization(Reporting Laboratory)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationrequestplacer" target="_blank">Organization(Test Request Placer)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationspecimencollector" target="_blank">Organization(Specimen Collector)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationdestination" target="_blank">Organization(Destination Laboratory)</a>


* <a href="https://simplifier.net/ontariolaboratoriesi/organizationassigner" target="_blank">Organization(Identifier Assigner)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/organizationrequesting" target="_blank">Organization(Requesting)</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/encounter" target="_blank">Encounter</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/operationoutcome" target="_blank">OperationOutcome</a>

* <a href="https://simplifier.net/ontariolaboratoriesi/bundle" target="_blank">Bundle</a>



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

**GET DiagnosticReport Without PHI**

Dates parameter: **issued**

* Example 1 : `issued=ge2016-01-02`

* Example 2: `issued=ge2015-02-25&issued=le2016-02-27`

Dates parameter: **specimen.collected**

* Example : `specimen.collected=ge2016-01-02`

Test Request code: **result.based-on:ProcedureRequest.code**

* Example: `result.based-on:ProcedureRequest.code=[code-system-local-base] /lab/test-request-codes|TR11663-2`

Interpretation parameter:**result.interpretation**

* Example 1: `result.interpretation=AB`
* Example 2: `result.intepretation=CR`

**Note:** This parameter allows the requestor to further restrict the search criteria to retrieve all abnormal results (AB) or critically abnormal only (CR).

Observation status: **result.status**

* Example: `result.status=final`

Observation code: **result.code**

* Example: `result.code=http://loinc.org|2028-9`

Diagnostic report identifier: **identifier**

* Example: `identifier=[id-system-local-base]/lab/report-id-lab-license-4004|543321`

Size limit (for response paging):**_count**

* Example:` _count=10`

If there is no _count in the search request, the server will return all matching records in one response.

<br>


Server will generate and return an additional parameter search-id as per Server Conformance section above.

* Example: `search-id=017-11-16T20:37:03.0000000X128987`

<br>

Format: JSON (default) or XML

* Example: `format=[mime-type]:_format=application/fhir+json` or `_format=application/fhir+xml`

<br>

## Example

**Diagnostic Report Search Example**

<br>

`GET [base]/DiagnosticReport?issued=ge2016-01-02&_count=10`

<br>

In the returned header:`[base]/DiagnosticReport?issued=ge2016-01-02 &_count=10&search-id=017-11-16T20:37:03.0000000X128987`

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
| Practitioner(Ordering, Performing and Reporting Practitioner)         |   <a href="https://simplifier.net/OntarioLaboratoriesI/Practitioner-example/" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Practitioner-example/~json/~xml" target="_blank"> JSON</a>          |                        
| Practitioner(Copied to, Attending and Admitting Practitioner)         |  <a href="https://simplifier.net/ontariolaboratoriesi/practitioner-example-2/~xml" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Practitioner-example-2/~json" target="_blank"> JSON</a>          |                        
| Organization(Performing and Reporting Laboratory, Ordering Facility)        |  <a href="https://simplifier.net/ontariolaboratoriesi/organization-example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Organization-example/~json" target="_blank"> JSON</a>         |                        
| Organization(Destination Laboratory, Specimen Collector, Test Request Placer Organization and Requesting Organization)         |   <a href="https://simplifier.net/ontariolaboratoriesi/organization-example-2" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Organization-example-2/~json" target="_blank"> JSON</a>          |    
| Organization(Identifier Assigner)         |   <a href="https://simplifier.net/ontariolaboratoriesi/organization-example-3" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Organization-example-3/~json" target="_blank"> JSON</a></a>          |   
| Encounter         |   <a href="https://simplifier.net/ontariolaboratoriesi/encounter-example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/Encounter-example/~json" target="_blank"> JSON</a>          |   
| OperationOutcome         |   <a href="https://simplifier.net/OntarioLaboratoriesI/OperationOutcome-example/~xml" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/OperationOutcome-example/~json" target="_blank"> JSON</a>          |                       
                    
