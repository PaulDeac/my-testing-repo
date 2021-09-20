### JWT Business Data

The following table summarizes the mandatory information that needs to be supplied by the consumer to authorize the request.

Table 6- JWT Query Data

| Data Element | Definition    | Example       | 
|----------|---------------|-----------------|
| User Id    | This parameter should contain the user id/system id or login id unique to each user in the consuming system | Email User Id: jasmith@myhealthapp.com System User Id: mjones1234|
| User Full Name    | This parameter should contain the consuming user's full name captured by the Consuming Application | John Alexander Smith, Mary Jones,              Mr. Jake Smith Jr.|
| Access Request Type    | This parameter should contain the type of user submitting the query. 'P' identifies the Patient and 'D' identifies a delegated user authorized by the patient3 | P or D |