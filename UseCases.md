<p id="breadcrumb">

[Business Context](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemProviderQuery/BusinessContext) > Use Cases

</p>



# Use Cases


The use cases below provide a basic illustration of how different actors interact with OLIS using the Provider Query with the basic flow.
## Participants

**Table: Use Case Participants**


| Participant | Type   | Description |
|-
| Health Care Provider | Human  | A person such as the health care provider who interacts with the system via a health care provider application to search a person’s laboratory information in OLIS based on the Ontario Health card. |
| Health care Provider Application | System | A web based application (handheld device, web or portal), used by the health care provider to search lab information in OLIS. The application maintains, manages and validates the user information and credentials, prior to the request being sent to OLIS. |
| Provider  Gateway | System | An interface layer that processes security and user based information received from a health care provider application. The Provider Gateway authorizes the query be processed by OLIS. |
| OLIS | System | The EHR asset that receives the request, processes the query, and returns the results. |

## UC1 – OLIS health care provider requests lab information and retrieves the request

An authorized Health Care Provider uses their Health Care Provider Application to search OLIS for their lab information.

**Table: Use Case #1**


| Step | Description |
|-
| 0. | Health care provider enters the search criteria for the search in the Health Care Provider  Application to look up lab information based on the Ontario Health Card Number |
| 1.   | Health Care Provider Application authenticates the validity of the Health Care Provider requesting the query as well as ensures that the request is valid, and all mandatory criteria provided. The application then formulates the request and submits it to the Provider gateway and OLIS. |
| 2.   | Provider gateway receives the request, ensures the requested information is available for authorization and records the information prior to authorizing OLIS to process the request. |
| 3.   | OLIS receives the request, validates, processes the query and returns the result back to the Health Care Provider via the Provider gateway. |
| 4.   | Provider gateway processes the response back to the Health Care Provider  Application. |
| 5.   | Health Care Provider  Application displays the information received by the Provider gateway back to the Health Care Provider. |
| 6.   | Health Care Provider reviews the information and might choose to store the information locally (if applicable). |

## Alternate flows (not expanded) include:

i. Provider gateway fails to authorize the request (e.g. missing required information). Negative response returned to the Health Care Provider.
ii. Invalid parameter information (including incorrect format, blank value provided for parameter) provided in the request. Negative response returned to the Health Care Provider.

## UC2 – HIC organization requests lab information and retrieves the request

An authorized Health Information Custodian uses their organization application to search OLIS for their lab information.

**Table: Use Case #2**


| Step | Description  |
|-
| 0.   | User enters the search criteria for the search in the HIC organization  Application to look up lab information based on the Ontario Health Card Number. |
| 1.   | HIC organization Application authenticates the validity of the Health Care Provider requesting the query as well as ensures that the request is valid, and all mandatory criteria provided. The application then formulates the request and submits it to the Provider gateway and OLIS. |
| 2.   | Provider gateway receives the request, ensures the requested information is available for authorization and records the information prior to authorizing OLIS to process the request. |
| 3.   | OLIS receives the request, validates, processes the query and returns the result back to the Health Care Provider via the Provider gateway. |
| 4.   | Provider gateway processes the response back to the HIC organization  Application. |
| 5.   | HIC organization  Application displays the information received by the Provider gateway back to the Health Care Provider. |
| 6.   | Health Care Provider reviews the information and might choose to store the information locally (if applicable). |

## Alternate flows (not expanded) include:

i. Provider gateway fails to authorize the request (e.g. missing required information). Negative response returned to the Health Care Provider.
ii. Invalid parameter information (including incorrect format, blank value provided for parameter) provided in the request. Negative response returned to the Health Care Provider.



