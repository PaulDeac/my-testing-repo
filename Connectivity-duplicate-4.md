<p id="breadcrumb">

[Implementation Guidance](https://simplifier.net/guide/OntarioLaboratoriesInformationSystemConsumerQuery/ImplementationGuidance) > Connectivity

</p>


# Connectivity

## JWT Business Data

The following table summarizes the mandatory information that needs to be supplied by the consumer to authorize the request.

**Table: JWT Query Data**



| Data Element     | Definition                                                                                         | Type | Optionality | Length | Example                          |
|------------|---------------------------------------------------------------------------------------------------------|------|-------------|--------|----------------------------------|
| jti        | Unique Token ID- will be generated by application                                                       | ST   | Mandatory   | 1..40  |                                  |
| org        | The name of original organization the application is associated with                                    | ST   | Optional    | 1..70  | University Health Network        |
| app        | The name of application used for the access                                                             | ST   | Mandatory   | 1..50  | Medly                            |
| appVersion | The version of the application                                                                          | ST   | Mandatory   | 1..10  | 1.03                             |
| sub        | The login ID of the user initiating the login request                                                   | ST   | Mandatory   | 1..50  | jasmith@myhealthapp.com          |
| idp        | Identify provider- work with eHealth Ontario to assign IDP                                              | ST   | Mandatory   | 1..255  | http://ehealthontario.ca/fhir/NamingSystem/idp-medly |
| prn        | Name of the user (principal , as defined in https://openid.net/specs/draft-jones-json-web-token-07.html | ST   | Mandatory   | 1..75  | John Smith                       |
| userType   | Type of the user, P (patient) or D (delegate).                                    | ST   | Mandatory   | 1..10  | P            |
aud   | Identifier of the user. Should represent the same value as the one present in the FHIR query string                                  | ST   | Mandatory   | 1..90  |             |
exp   | Token expiration time (Its value is a JSON number representing the number of seconds from 1970-01-01T0:0:0Z as measured in UTC until the date/time.)                                 | NM   | Mandatory   | 1..20  |             |
iat  | Issued time (Its value is a JSON number representing the number of seconds from 1970-01-01T0:0:0Z as measured in UTC until the date/time.)                                  | NM   | Mandatory   | 1..20  |  1444143566          |


**JWT Header**



| Data Element     | Definition                                                                                         | Type | Optionality |
|------------|---------------------------------------------------------------------------------------------------------|------|-------------|
| alg      | Algorithm used.  As defined in https://tools.ietf.org/html/rfc7515#page-10 This has to be set to  "RS256"                                                       | ST   | Mandatory   |
| kid       | Key ID used to secure the token, as defined in https://tools.ietf.org/html/rfc7515#page-11                                    | ST   | Optional    |
| x5t     | Certificate thumbprint used to sign the token, as defined in https://tools.ietf.org/html/rfc7515#page-12                                                      | ST   | Mandatory   |
| typ    | Type of the token. As defined in: https://tools.ietf.org/html/rfc7515#page-12 always set to “JWT”                                  | ST   | Mandatory    |
