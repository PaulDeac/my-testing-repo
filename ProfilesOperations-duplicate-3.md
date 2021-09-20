<p id="breadcrumb">

[Table of Contents](https://simplifier.net/guide/ontariolaboratoriesinformationsystemconsumerquery/home) > Profiles & Operations

</p>

# Profiles & Operations

## Resources

Resources are the building blocks of the FHIR® standard.  These resources convey the content of clinical records, identify patients or providers, or otherwise support messaging between systems. These resources have been developed by several working groups at HL7, based on members’ experience and subject expertise.  These resources are intended to capture and support 80% of all implementation use case requirements; projects are encouraged to meet the remaining 20% of requirements through extensions and profile constraints. The list of all available resources in the FHIR® standard can be found at https://hl7.org/fhir/resourcelist.html, with additional details at https://hl7.org/fhir/resourceguide.html.

## Profiles

Resources defined in the FHIR® standard are intended to support a wide variety of use cases, resulting in a large number of available elements, and very few constraints. Implementers are encouraged to create and apply FHIR®  Profiles, which places constraints on the defined FHIR®  resources – tightening cardinality, identifying unused/unsupported elements, defining value sets for elements, and adding extension elements.

## Operations

The table below shows the allowed transactions on FHIR® resources and their corresponding HTTP operations:

**Table: OLIS FHIR® HTTP Operations**

|Operation|Resource|HTTP Verb|
|-
|[DiagnosticReport Search](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemConsumerQuery/DiagnoticReportSearch)|DiagnosticReport|GET|
