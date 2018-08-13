![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

Employee Details (ED) Software Development Kit (SDK)
=======================================

Key Features:
-------------

- Simulating Employee Details (ED) filing operations
	- Test Scenarios
	- Test Data
    - Message samples (positive responses)
    - Schema Validation
    - Error Handling (Not Included)
	
- Schemas and WSDLS
	- View and download the [common xsd](../../Schema%20-%20Common/)
	- View and download the [return service common xsd](../../Service%20-%20Return/Latest/)
	- View and download the Employee Details (ED) [xsd](Employment.xsd) and [wsdl](EmploymentDevWsdl.wsdl) from this current directory
	
- Employment Service 
	- [Download the build pack](Gateway%20Services%20Build%20Pack%20-%20Employment%20Service.pdf) to view data definitions of each operation and response status code definitions
	
- OAuth Authentication 
	- [How to Integrate with OAuth](ED_Auth_Access_Token_Steps.md)
	- [Sample curl commands - for testing the OAuth flow](ED_Auth_Access_Token_Steps.md)

- Identity and Access Service 
	- [Download the build pack](../../Service%20-%20Identity%20and%20Access/Latest/) for OAuth 2.0 implementation 

Features Details:
-----------------

- Test Scenarios
	![Test Scenarios](images/Emulated_Services_Coverage_Map-Return_ES.png)

- Test Data
This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses. Text in italics represents the name of the XML node in the request.
	**To Add**
	
	Operation | Scenario ID | Data | 
	RetrieveList | EMS_ES081 | Employee IRD (identifier): 123114116
	Update | EMS_ES096 | Employee IRD (identifier): 123183711
	Create | EMS_ES095 | Employee IRD (identifier): 123183711
	Update | EMS_ES099 | employmentStartDate: today's date
        
- Message samples - simulating Employment Service Operations:
    - Create
        - Positive response
            - [request sample](sample%20messages/body-employment-create-request.xml)
            - [response sample](sample%20messages/body-employment-create-response.xml)
    - Terminate
        - Positive response
            - [request sample](sample%20messages/body-employment-terminate-request.xml)
            - [response sample](sample%20messages/body-employment-terminate-response.xml)
    - Update
        - Positive response
            - [request sample](sample%20messages/body-employment-update-request.xml)
            - [response sample](sample%20messages/body-employment-update-response.xml)
    - RetrieveList
        - Positive response
            - [request sample](sample%20messages/body-employment-retrievelist-request.xml)
            - [response sample](sample%20messages/body-employment-retrievelist-response.xml)

            
Requests Matching Logic
-----------------------

- ReadMe Page - (default) port 8080 of root path of Welcome Page, you are already here
- Authentication mappings - (default) port 8443 of following paths:
    - /ms_oauth/oauth2/endpoints/oauthservice/authorize
    - /oam/server/auth_cred_submit
    - /ms_oauth/oauth2/endpoints/oauthservice/tokens
- Returns Service Mappings - (default) port 8080 of path "/gateway/GWS/Returns":
    - /gateway/GWS/Returns?wsdl - wsdl is not available, returning http 200 only
    - /gateway/GWS/Returns - Authentication validation will be performed at first:
        - if fail then return Authentication Errors
        - if pass then:
            - XML validation will be performed:
                - if fail then return XML Validation Errors
                - if pass then return positive responses
- Default Mapping - Very last matching logic to handle all other requests by returning 404 error when no matching found