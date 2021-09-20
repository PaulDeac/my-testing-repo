<p id="breadcrumb">

[Home](Home) > Identifier Policy

</p>


# Identifier Policy

The OLIS FHIR Patient Query For Providers project uses URIs whenever Object Identifiers are required. URIs (Uniform Resource Identifiers) are globally unique identifiers for individual objects, as well as for value sets, code systems, profiles, namespaces, and more. URIs is the preferred object identifiers for FHIR objects, and is usually represented as URLs. All URIs used in eHealth Ontario projects must conform to eHealth Ontario's URI Management Policy.

For more information, or to obtain the proper URLs for use in this project, contact the eHealth Ontario Architecture & Standards Division at architecture@ehealthontario.on.ca 

The base URL for OLIS FHIR® interface will be referred to as "[base]" in the sections and examples below. These identifiers capture the URI specific to an implementation/environment, such as the URL for resources and extensions used in the OLIS solution.


The base for global identifier namespaces (e.g. Ontario health card number, Ontario Physician License, etc.) will be referred to as "[id-system-global-base]" throughout the specification.
The base for local identifier namespaces (e.g. placer group number, order number, etc.) will be referred to as "[id-system-local-base]" throughout the specification. 
The base for local code systems (e.g. test request code) will be referred to as "[code-system-local-base]" throughout the specification.
Due to the evolving FHIR standard and its developing framework and governance, implementers should recognize that these identifiers may change if identifier registration becomes governed nationally or internationally. Implementers are recommended to implement URIs using configurable variables.

**Table: Identifier Variables**

|Variable|Value|
|-
|[base]|	https://provider.ehealthontario.ca:9443/api/fhir/stu3/v1/DiagnosticReport 
|[base-structure]|http://ehealthontario.ca/fhir/StructureDefinition |
|[id-system-global-base]|	https://fhir.infoway-inforoute.ca/NamingSystem |
|[id-system-local-base]|http://ehealthontario.ca/fhir/NamingSystem |
|[code-system-local-base]|	http://ehealthontario.ca/fhir/NamingSystem |