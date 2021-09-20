### Context
The OLIS Consumer Lab Reports Query provides backend interface to the consumer applications and portals to allow a consumer to view their lab data in OLIS. The query also allows authorized delegated user(s) to access the lab reports on behalf of the consumer. 

The Consumer Application shall be responsible for the onboarding, management, upkeep and maintenance of the users as well as the delegated user. The Consumer Application shall manage rules around access for a delegated user to view OLIS data on behalf of a consumer. This includes but not limited to rules around authenticating a user prior to submitting the query to OLIS as well as requirements around the ability of a delegated user to view OLIS data before the patient's ability to view the data themselves. 

The consumer application shall ensure that the required auditing information for the user is provided to the OLIS Consumer Query interface to maintain traceability and comply with privacy and auditing requirements. 



### Query Functionality

In order to comply with auditing and privacy requirements, the Consumer Application should provide the following information with every request

•             Hands at the keyboard

•             Access Request Type   

•             HIC Organization responsible for enrolling the user 

•             Name of the Computer application being used by the user to access the data.




### The mandatory parameters for the query:

•	Patient Health Card Number

•	Gender 

•	Date of birth




### The optional parameters for the query:
•	Placer Group Number

•	Test Request Code

•	Test Result Code

•	Observation status 

•	Abnormal Flag

•	Continuation pointer

•	End Date (this should default to either Observation Date or Last Updated Time in OLIS that the consumer has chosen for the Start Date)

