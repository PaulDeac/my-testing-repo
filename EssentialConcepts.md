<p id="breadcrumb">

[Essential Concepts](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemConsumerQuery/EssentialConcepts) > Essential Concepts

</p>


# Essential Concepts
This section describes a number of the most significant aspects of the OLIS system and how external systems communicate with OLIS using FHIR. In order to parse the lab reports from OLIS FHIR interface,  clients need to know the business rules in order to interpret the information in these scenarios:

•	when they receive new results

•	when they receive an updated result (amended Test Result)

•	when they receive a FULL REPLACE report where they have to remove all test requests and assoicate test results from a report that was previously submitted and replace it with the incoming report 

•	when they receive Microbiology Test request replace  replace amendment

In all these scenarios, the search result may contain multiple lab reports, test requests, and test results. To interpret and present data properly, it is important to understand how to uniquely identify these entities. This section explains how to do this.

## Non-Nominal Testing

OLIS supports non-nominal testing (e.g. HIV tests), in which the identity of the patient is known only to the ordering practitioner. For non-nominal testing, the HIC provides OLIS with a facility-generated ID for the patient. No other patient identifiers (besides facility-generated ID) are transmitted to OLIS with the order/report.  

## How to Uniquely Identify entities in OLIS FHIR

Since OLIS FHIR query is RESTful search operation, the result is a bundle that may contain multiple lab reports. Each lab report may contain multiple test requests and test results. Below is how to identify these entities:

**Lab Report**

**Test Request**

**Test Result**

A test result is uniquely identified in OLIS by the following fields: 

• Placer Group Number (Order/Report ID)

• Placer Order Number (Test Request Identifier)

• Observation Identifier (Test Result Code)

• Observation Sub-ID

• Test Result Release Date/Time

## Full Replace Amendment 

Full Replace Amendment is an additional amendment mechanism in OLIS to support complex amendment scenarios. One such scenario is the case where the laboratory needs to report fewer observations for a test request than it had previously submitted or to remove a test request and all related results from a report that it had previously submitted. 

Clients who retrieve and store lab reports from OLIS (e.g., EMRs, the electronic Child Health Network, and Cancer Care Ontario) must ensure that when they receive an amended report from OLIS, that they store it in its entirety as a replacement of the prior version of the report.

## Test Request Replace Amendment 

Test Request Replace Amendment is an additional amendment mechanism in OLIS to support complex amendment scenarios specifically to replace parent-child relationships. This functionality is only used for Microbiology modality. The functionality can be used to perform a replace of all corresponding children test request(s) and test result(s) for a particular parent with a new subset. 

Clients who retrieve and store lab reports from OLIS (e.g., EMRs, the electronic Child Health Network, and Cancer Care Ontario) must ensure that when they receive an amended report from  OLIS, that they store it in its entirety as a replacement of the prior version of the report. For resulted orders only the report with the latest test result is returned. 
When a laboratory amends a test result in OLIS, it submits a later Test Result Release Date/Time value to indicate to OLIS that the result amends and replaces the previously reported value.

