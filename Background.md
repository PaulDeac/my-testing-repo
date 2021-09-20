## Background
Ontario Laboratories Information System (OLIS) is the single provincial system that allows all laboratory information on patients in Ontario to exchange electronically between practitioners and laboratory service providers and provides the Ministry of Health and Long-Term Care (MOHLTC) with program management information. OLIS facilitates the exchange of laboratory information on human beings in Ontario amongst LIS, HIS, EMR and other point of service systems (POS), but it is not a LIS system in its own right, and is not intended to replace existing LIS systems. 

OLIS has an existing HL7 v2 interface that is used by labs to submit laboratory results as well as an inquiry interface that allows authorized clinicians to access lab results via EMR’s, regional and standalone clinical viewers. In order to address the growing need by Consumer Applications and Portals to be able to view OLIS data; a RESTful FHIR®  interface is being introduced that enables consumer oriented portals and apps to access lab results from OLIS for a consumer.  The interface also supports the ability for a patient or consumer to share their information with caregivers as a delegated user. This interface can be consumed by leveraging the OLIS Consumer Lab Reports Query by a variety of clients from traditional portals and EMR’s to mobile apps and devices.

While the information retrieved via patient access and provider access interface is identical for a given patient in many cases, the business rules related to processing these two requests are different in terms of, consent application, audit generation, consent overrides and notification.

*Table 1 - Service Endpoints and Standards*

| Function | Messaging     | Transport       | Security  |
|----------|---------------|-----------------|-----------|
| Query    | HL7 FHIR STU3 | REST over HTTPS | PKI / JWT |

Note:

Public Key Infrastructure (PKI) certificate (i.e. HTTPS) and Jason Web Token (JWT) token.

PKI: PKI certificate required

JWT: JWT token required




