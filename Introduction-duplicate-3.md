<p id="breadcrumb">

[Home](Home) > Introduction

</p>

# Introduction

## Background

Ontario Laboratories Information System (OLIS) is the single provincial system that allows all laboratory information on patients in Ontario to exchange electronically between practitioners and laboratory service providers and provides the Ministry of Health and Long-Term Care (MOHLTC) with program management information. OLIS facilitates the exchange of laboratory information on human beings in Ontario amongst Laboratory Information System (LIS), Hospital Information System (HIS), Electronic Medical Record (EMR) and other point of service systems (POS), but it is not a LIS system in its own right, and is not intended to replace existing LIS systems.

OLIS has an existing HL7 v2 interface that is used by labs to submit laboratory results as well as an inquiry interface that allows authorized clinicians to access lab results via EMR’s, regional and standalone clinical viewers. 

A RESTful FHIR® interface is being introduced that enables health care provider oriented portals and apps to access lab results from OLIS for their patients. This interface can be consumed by leveraging the OLIS FHIR Patient Query for Providers by a variety of clients from traditional portals and EMR’s to mobile apps and devices.

While the information retrieved by the health care provider access interface using the RESTful FHIR® interface is identical to what would be retrieved using the current HL7 based patient query in many cases, the business rules related to processing these two requests are different in terms of, consent application, audit generation, consent overrides and notification.


**Table: Service Endpoints and Standards**

| Function | Messaging     | Transport       | Security  |
|----------|---------------|-----------------|-----------|
| Patient Query For Providers    | HL7 FHIR STU3 | REST over HTTPS | PKI / JWT |

Note:

Public Key Infrastructure (PKI) certificate (i.e. HTTPS) and Jason Web Token (JWT) token.

PKI: PKI certificate required

JWT: JWT token required

## Copyright Notice

This specification is fully copyright protected by the owner. The owner has the exclusive right to make copies of this specification. No alterations, deletions or substitutions may be made without the prior written consent of the owner. No part of it may be reproduced or transmitted in any form or by any means, electronic or mechanical, including photocopy, email or any information storage and retrieval system, without the prior written consent of the owner.

HL7® is registered trademark of Health Level Seven, Inc. (http://www.hl7.org) This specification contains information for which copyright is held by Health Level Seven, Inc. Implementors of the standards (those developing software or otherwise making use of the specification) are required to be members of either Health Level Seven Inc., HL7 Canada or one of the other HL7 affiliates. There is no such membership requirement for individuals and organizations which merely install or use software with built-in HL7 interfaces.

LOINC® is a registered trademark of the Regenstrief Institute, Inc. (http://regenstrief.org)

This material includes SNOMED Clinical Terms® (SNOMED CT®) (https://www.snomed.org/snomed-ct/) which is used by permission SNOMED International. All rights reserved. SNOMED CT®, was originally created by The College of American Pathologists.

“SNOMED” and “SNOMED CT” are registered trademarks of the SNOMED International (https://www.snomed.org/) .

**Disclaimer**

This specification contains proprietary and confidential information of eHealth Ontario (“eHealth”). This specification is offered to you on the condition that you accept these terms and conditions without modification. Any dissemination or distribution of this specification or any copies thereof to any third party without eHealth’s prior written consent is strictly prohibited.

eHealth has prepared this specification for its own use and provides it to you for information purposes only. You understand that the information in this specification may be subject to change at any time and that eHealth cannot be responsible for the completeness, currency, accuracy or applicability of this specification, or any information contained in it, to your needs or the needs of any other party. You understand and agree that:

(i) you are solely responsible for determining whether any information in this specification is applicable to your needs;

(ii) any access, use or reliance on any information in this specification is at your sole and exclusive risk;

(iii) this specification is provided “AS IS” without any warranties or representations of any kind, express or implied, in fact or in law;

(iv) eHealth is not responsible for your use or reliance on the information in this specification or any costs associated with such use or reliance; and

(v) eHealth has no liability to any party for that party’s access, use or reliance on this specification or any of the information contained in it.

**Document Control**

The electronic version of this specification is recognized as the only valid version.

**Approval History**

|APPROVER(S)|APPROVED DATE
|-
|Business and Technical Committee|2019-06-19|


