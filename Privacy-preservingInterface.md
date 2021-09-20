## Privacy-preserving Interface

This page describes the functionality of the privacy-preserving interface to OLIS. This interface promotes improved privacy for EHR access by enabling access to OLIS without using Personal Health Information (PHI) in FHIR query. 

### Background
Currently OLIS patient query must contain patient PHI such as patient health card number, gender and date of birth, in the search query parameter. This introduces privacy risk as patient PHI in the query will be exposed in user system and Ontario Health components. The privacy-preserving interface allows users to query OLIS without specifying PHI by adopting external trusted user ID store and other components. Patient PHI will be resolved internally and they will be protected to facilitate better privacy.

### Interface overview
The table below illustrates the generic information about this interface.

| Interface Property | Description  |
|-
| Name | OLIS FHIR privacy-preserving |
| Type | RESTful |
| Message Protocol | FHIR |
| Transport Protocol | HTTP |
| Endpoint | TBD |
| Error Codes | [Confluence link ](https://ehealthontario.atlassian.net/wiki/spaces/OAG/pages/256083012/Consumer+Gateway+Http+Error+Codes). This will be changed to point to the gateway documentation |

### PHI-less OLIS FHIR Query
To invoke a PHI-less OLIS FHIR query, please refer to [here](DiagnosticReportSearch)

