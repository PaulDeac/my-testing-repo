<p id="breadcrumb">

[Profiles & Operations](ProfilesOperations) > DiagnosticReport Search

</p>

# DiagnosticReport Search - COVID19 Query For Public Health Units

DiagnosticReport search is simple RESTful interaction. It supports retrieving lab results from OLIS for specific disease such as COVID19.

## Scope

This transaction involves a request by the following parameters:

**The mandatory parameters for the query:**
* Start Date

The OAuth token must also contain the COVID19 scope. The scope value must include "filter/covid-19".


**The optional parameters for the query:**

* Maximum number of records to return


## Specification

The OLIS FHIR COVID Query is based on the HL7 STU3 Search operation.  

<br>


**Diagnostic Report Search Request**

The Diagnostic Report Search Request is an HTTP GET operation with multiple query parameters specified in Supported Search Parameters section below. The syntax of the request is 


`GET [base]/ DiagnosticReport?&issued=(ge|gt|le|lt)[date][&_count=[num]]`



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

**GET DiagnosticReport (return all COVID19 results issued after specific date)**

Dates parameter: **issued**

* Example 1 : `issued=gt2016-01-02`

* Example 2: `issued=gt2015-02-25&issued=lt2016-02-27`

Size limit (for response paging):**_count**

* Example:` _count=10`

If there is no _count in the search request, the server will return all matching records in one response.

<br>

Server will generate and return an additional parameter search-id as per Server Conformance section above.

* Example: `search-id= 017-11-16T20:37:03.0000000X128987`

<br>

Format: _format parameter is not supported. Including this parameter in the request will result an error. Note that COVID query only supports JSON. XML is not used.



<br>

## Example

**Diagnostic Report Search Example**


`GET [base]/DiagnosticReport?issued=gt2016-01-02&_count=10`

<br>


In the returned header:

`[base]/DiagnosticReport?&issued=gt2016-01-02&_count=10&search-id=017-11-16T20:37:03.0000000X128987`


**Examples of a search response can be found below**

| Resource | Example        |                                                                                      
---------------|-----------------------|
| DiagnosticReport example representing a positive COVID report        |  <a href="https://simplifier.net/OntarioLaboratoriesI/DiagnosticReport-COVID-Positive-Example" target="_blank"> XML</a> / <a href="https://simplifier.net/OntarioLaboratoriesI/DiagnosticReport-COVID-Positive-Example/~json" target="_blank"> JSON</a>          |    
| Bundle example representing searchset with one positive COVID Report        |  <a href="https://simplifier.net/ontariolaboratoriesi/bundle-example-covid-query" target="_blank"> XML</a> / <a href="https://simplifier.net/ontariolaboratoriesi/bundle-example-covid-query/~json" target="_blank"> JSON</a>         |   
| Patient with Anonymous Identifier        |   <a href="https://simplifier.net/ontariolaboratoriesi/patient-anon-id-example/~xml" target="_blank"> XML</a> / <a href="https://simplifier.net/ontariolaboratoriesi/patient-anon-id-example/~json" target="_blank"> JSON</a>          |     