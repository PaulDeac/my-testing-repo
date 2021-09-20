<p id="breadcrumb">

[Business Context](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemConsumerQuery/BusinessContext) > Business Rules

</p>


# Business Rules

The following Business rules should be considered for implementation: 

**Table: Business Rules**

| Business Rules # | Business Rule Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | FHIR®  field /JWT token                                                                                                                                                                                                                                        |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| UC1-101          | The patient information provided in the query must be accurate according to the most recent Ontario Health Card or medical record number.    | Patient.identifier                                                      |
| UC1-102          | A query request should not contain both specimen.collected and issuedDate parameters.   |specimen.collected or issued  |
| UC1-103          | When using End Date, End Date should be greater than the Start Date and should follow the equivalent parameter as in Start Date. | specimen.collected or issued |
| UC1-104          | Any parameters chosen in the filtering criteria should not have a blank value.  | All parameters |
| UC1-105          | On encountering a Patient or Test Request level block; the following warning message must be populated along with the warning code 980: “Please note your personal health information is blocked by a consent directive that restricts health care providers from viewing this information. Please advise your delegated users if you do not want them to share this information with others.”  | ProcedureRequest.extension (Test Request Level Block) returns a boolean value ‘true’ when a Test Request level block is populated. Note: The consumer application will automatically receive the warning code and message from OLIS for a patient level block. |
| UC1-106          | User Id should be unique to the consuming application and issuing organization.  The issuing organization should ensure that the user is valid and logs maintained for traceability purposes.   |  |
| UC1-107          | User Full Name should contain a valid full name of the user accessing the system. This includes first, second and last name; also designation and suffix if applicable.  |   |
| UC1-108  | The Access User Type should contain the type of user accessing the consumer application for OLIS. The parameter should be populated with either ‘P’ or ‘D’. A user accessing their personal lab information in OLIS is represented by ‘P’ for Patient. A user granted access and authority by a patient to access the patient’s information in OLIS is considered a ‘Delegate User’ and is represented by ‘D’. Note: Consuming applications should have proper policies in place to maintain users. |   |
| UC1-109  | The field lengths and requirements for data elements stated in the OLIS Interface Specification should be considered | All fields                    

                                                      
##  Search Query UC1    

Retrieves lab reports for a consumer based on selected criteria.

**Table: Search Criteria**   


{{tree:OntarioLaboratoriesI/OLISSearchCriteria.png/~overview}} 


**M** = Mandatory

**O** = Optional

**MX** = One of either issued or specimen.collected must be submitted. Each of the parameters support the submission of an open-ended time frame (start time only) or a closed timeframe (start and end).

**Y1** = Up to 100 codes may be submitted.

**Y2** = Up to 200 codes may be submitted.

    OLIS interprets multiple values submitted in a single parameter to be logically OR’d.

    Complex parameters are identified in the second row of the table. Refer to the previous pages for detailed definition of complex parameters.
                                                                                                                                            