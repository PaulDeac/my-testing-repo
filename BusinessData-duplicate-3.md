[Business Context](BusinessContext)  > Business Data

</p>


# Business Data

The list of data elements, description and requirements that data providers adhere to for OLIS data, can be found in the latest version of the OLIS Interface Specification for OLIS HL7 v2. Viewers querying OLIS data should consider the requirements.


## Query Parameters Data

### OLIS FHIR Patient Query For Providers Parameters Data
The following table summarizes the mandatory and optional parameters for the OLIS FHIR Patient Query For Providers

**Table: OLIS FHIR Patient Query For Providers Parameter Data**

**Mandatory Parameters:**


| Data Element       | Definition    | Example        |
|-
| Patient Identifier | This parameter should contain the 10 digit Ontario Health Card Number for the patient  | 3821694372     |
| Patient Birthdate  | This parameter should contain the Date of Birth of the patient as on the Ontario Health Card | 1929-11-29     |
| Patient Gender     | This parameter should contain the sex at birth as noted on the Ontario Health Card | male or female |
| Start Date   | This parameter should contain the start date of the search criteria. The date can either be the date that OLIS received the report (issued), or the date that the test was performed (specimen.collected). | 2018-04-02   |

**Optional Parameters:**

| Data Element        | Definition  | Example           |
|-
| End Date            | This parameter contains the end date of the search criteria if required. The end date should be the same parameter as the start date parameter for the query. Note: Not selecting this parameter defaults to current date and time.                     | 2018-04-15                                           |
| Observation Code    | This parameter allows the requestor to further restrict the search criteria to certain test result code(s). Code(s) selected must be valid in the most recent OLIS Test Result Nomenclature file. No more than 200 codes should be selected in a query. | 718-7                                                |
| Test Request Code |This parameter allows the requestor to further restrict the search criteria to certain test request code(s). Code(s) selected must be valid in the most recent OLIS Test Request Nomenclature file. No more than 100 codes should be selected in a query.    | TR11663-2 |
| Observation Status  | This parameter allows the requestor to further restrict the search criteria to test result(s) status of interest | Preliminary, Final, Corrected, Cancelled, Registered |
| Abnormal Flag Code  | This field allows the requestor to further restrict the search criteria to retrieve results that are abnormal (including critically abnormal) or critically abnormal.  | ‘AB’ for Abnormal or ‘CR’ for Critically abnormal    |
| Diagnostic Report Identifier  | This field allows the requestor to further restrict the search criteria to retrieve results for a particular Lab Report Identifier or Placer Group Number.  |     |

### OLIS FHIR COVID Query Parameters Data
The following table summarizes the mandatory and optional parameters for the OLIS FHIR COVID query

**Table: OLIS FHIR COVID Query Parameter Data**

**Mandatory Parameters:**

|Data Element|Definition| Example |
|-
| Start Date | This parameter should contain the date that OLIS received the report (issued)| 2018-04-02 |

**Optional Parameters:**

|Data Element|Definition| Example |
|-
| _count| This parameter contains the maximum number of records that user wants to receive. This must be a positive integer value.| 10 |







