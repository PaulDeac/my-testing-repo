<p id="breadcrumb">

[Business Context](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemConsumerQuery/BusinessContext)  > Business Data

</p>


# Business Data

The list of data elements, description and requirements that data providers adhere to for OLIS data, can be found in the latest version of the OLIS Interface Specification for OLIS HL7 v2. Viewers querying OLIS data should consider the requirements.


## Query Parameters Data

The following table summarizes the mandatory and optional parameters for the query

**Table: Consumer Query Parameter Data**

**Mandatory Parameters:**


| Data Element       | Definition                                                                                                                                                                                                 | Example        |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|
| Patient Identifier | This parameter should contain the 10 digit Ontario Health Card Number for the patient or a medical record number issued by healthcare organization. When patient selects MRN to query by, they should also provide the healthcare organization identifier. | 3821694372     |
| Patient Date of BIrth  | The parameter should contain the Date of Birth of the patient related to the patient identifier entered. For example if an Ontario Health Card number was used the date of birth must match the Ontario Health Card. If a Medical Record Number (MRN) was used then the date of birth must be the same as the one noted for the MRN.  | 1929-11-29     |
| Patient Gender     | This parameter should contain the sex as noted relevant to the identifier used. | male or female |
| Start Date         | This parameter should contain the start date of the search criteria. The date can either be the date that OLIS received the report (issued), or the date that the test was performed (specimen.collected). | 2018-04-02     |

**Optional Parameters:**

| Data Element        | Definition                                                                                                                                                                                                                                              | Example                                              |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| End Date            | This parameter contains the end date of the search criteria if required. The end date should be the same parameter as the start date parameter for the query. Note: Not selecting this parameter defaults to current date and time.                     | 2018-04-15                                           |
| Observation Code    | This parameter allows the requestor to further restrict the search criteria to certain test result code(s). Code(s) selected must be valid in the most recent OLIS Test Result Nomenclature file. No more than 200 codes should be selected in a query. | 718-7                                                |
| Test Request Code |This parameter allows the requestor to further restrict the search criteria to certain test request code(s). Code(s) selected must be valid in the most recent OLIS Test Request Nomenclature file. No more than 100 codes should be selected in a query.                                                                                                                                       | TR11663-2 |
| Observation Status  | This parameter allows the requestor to further restrict the search criteria to test result(s) status of interest                                                                                                                                        | Preliminary, Final, Corrected, Cancelled, Registered |
| Abnormal Flag Code  | This field allows the requestor to further restrict the search criteria to retrieve results that are abnormal (including critically abnormal) or critically abnormal.                                                                                   | ‘AB’ for Abnormal or ‘CR’ for Critically abnormal    |
| Diagnostic Report Identifier  | This field allows the requestor to further restrict the search criteria to retrieve results for a particular Lab Report Identifier or Placer Group Number.                                                                                   |     |


