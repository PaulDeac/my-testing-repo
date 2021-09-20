<p id="breadcrumb">

[Implementation Guidance](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemConsumerQuery/ImplementationGuidance) > Consumer Responsibility

</p>

# Consumer Responsibility

## Privacy
The information which adopters receive when querying OLIS is considered Personal Information and Personal Health Information. As a result, access to the health patient information must be restricted to only appropriately authorized users and used on a need-to-know basis as specified in data-sharing agreements and corresponding legislation.

## User Credentials
In order to meet the privacy obligations, the audit records maintained at the service level need to know the details of the consumer application and the user making the request.
The sending application is expected to create a JSON Web Token with the relevant information and embed within the FHIR®  request as http header.	

## Message Validation
The consumer shall implement request messages that are well-formed and conform to this specification. 
