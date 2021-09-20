<p id="breadcrumb">

[Business Context](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemConsumerQuery/BusinessContext) > Use Cases

</p>


# Use Cases

The use cases below provide a basic illustration of how different actors interact with OLIS using the Consumer Query with the basic flow.
## Participants

**Table: Use Case Participants**


| Participant          | Type   | Description                                                                                                                                                                                                                                       |
|----------------------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Consumer             | Human  | A person such as the consumer or the delegate user who interacts with the system via a consumer application to search a person’s laboratory information in OLIS based on the Ontario Health card or medical record number.                                                 |
| Consumer Application | System | A web based application (handheld device, web or portal), used by the consumer to search lab information in OLIS. The application maintains, manages and validates the user information and credentials, prior to the request being sent to OLIS. |
| Consumer Gateway     | System | An interface layer that processes security and user based information received from a consumer application. The Consumer Gateway authorizes the query be processed by OLIS.                                                                       |
| OLIS                 | System | The EHR asset that receives the request, processes the query, and returns the results.                                                |

## UC1 – OLIS Consumer requests lab information and retrieves the request

An authorized consumer uses their consumer application to search OLIS for their lab information.

**Table: Use Case #1**


| Step | Description                                                                                                                                                                                                                                                          |
|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0.   | Consumer enters the search criteria for the search in the consumer application to look up lab information based on the Ontario Health Card Number or medical record number. |
| 1.   | Consumer Application authenticates the validity of the consumer requesting the query as well as ensures that the request is valid, and all mandatory criteria provided. The application then formulates the request and submits it to the Consumer Gateway and OLIS. |
| 2.   | Consumer Gateway receives the request, ensures the requested information is available for authorization and records the information prior to authorizing OLIS to process the request.                                                                                |
| 3.   | OLIS receives the request, validates, processes the query and returns the result back to the Consumer via the Consumer Gateway.                                                                                                                                      |
| 4.   | Consumer Gateway processes the response back to the Consumer Application                                                                                                                                                                                             |
| 5.   | Consumer Application displays the information received by the Consumer Gateway back to the Consumer.                                                                                                                                                                 |
| 6.   | Consumer reviews the information and might choose to store the information locally (if applicable)                                                                                                                                                                   |

## Alternate flows (not expanded) include:

i. Consumer Gateway fails to authorize the request (e.g. missing required information). Negative response returned to the Consumer.
ii. Invalid parameter information (including incorrect format, blank value provided for parameter) provided in the request. Negative response returned to the Consumer.



