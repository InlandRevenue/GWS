![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

Employment Information (EI) Returns Software Development Kit (SDK)
=======================================

Key Features:
-------------

- Simulating AIM filing operations
	- Test Scenarios
	- Test Data
    - Message samples (positive responses)
    - Schema Validation
    - Error Handling (Not Included)
	
- Schemas and WSDLS
	- View and download the [common xsd](../../Service%20-%20Common/)
	- View and download the [return service common xsd](../../Service%20-%20Return/Latest/)
	- View and download the Employment Income (EI) return [xsd](ReturnEI.v1.xsd) and [wsdl](ReturnsEIDevWsdl.wsdl) from this current directory
	
- Returns Service 
	- [Download the build pack](../../Service%20-%20Return/Latest/) to view data definitions of each operation and response status code definitions
	
- OAuth Authentication 
	- [How to Integrate with OAuth](EI_Auth_Access_Token_Steps.md)
	- [Sample curl commands - for testing the OAuth flow](EI_Auth_Access_Token_Steps.md)

- Identity and Access Service 
	- [Download the build pack](../../Service%20-%20Identity%20and%20Access/Latest/) for OAuth 2.0 implementation 

Features Details:
-----------------

- Test Scenarios
	[Test Scenarios](images/Emulated_Services_Coverage_Map-Return_EI.png)

- Test Data
This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses. Text in italics represents the name of the XML node in the request.
	**To Add**
	
	Operation | Scenario ID | Data | 
	Prepop | EMS_EI001 | Employer IRD (identifier): 123041607 periodEndDate: 2018-04-30 payDayDate 2018-04-10
	Prepop | EMS_EI002 | Employer IRD (identifier): 123094018 periodEndDate: 2018-12-31 payDayDate 2018-12-10
	RetrieveReturn | EMS_EI017 | Employer IRD (identifier): 123041607 periodEndDate: 2018-04-30 payDayDate 2018-04-10 submissionKey 987654321
	RetrieveReturn | EMS_EI017 | Employer IRD (identifier): 123094018 periodEndDate: 2018-12-31 payDayDate 2018-12-10 submissionKey 987654321
        
- Message samples - simulating EI Returns Operations:
    - PrePop
        - Positive response
            - [request sample](sample%20messages/body-ei-returnprepop-request.xml)
            - [response sample](sample%20messages/body-ei-returnprepop-response.xml)
    - File
        - Positive response
            - [request sample](sample%20messages/body-ei-returnfile-request.xml)
            - [response sample](sample%20messages/body-ei-returnfile-response.xml)
    - RetrieveStatus
        - Positive response
            - [request sample](sample%20messages/body-ei-returnstatus-request.xml)
            - [response sample](sample%20messages/body-ei-returnstatus-response.xml)
    - RetrieveFilingObligations
        - Positive response
            - [request sample](sample%20messages/body-ei-filingobligation-request.xml)
            - [response sample](sample%20messages/body-ei-filingobligation-response.xml)
    - RetrieveReturn
        - Positive response
            - [request sample](sample%20messages/body-ei-retrievereturn-request.xml)
            - [response sample](sample%20messages/body-ei-retrievereturn-response.xml)

            
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