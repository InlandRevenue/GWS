AIM Returns Software Development Kit (SDK)
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
	- [View and download the common xsd](../Service%20-%20Common/)
	- [View and download the return service common xsd](../Service%20-%20Return/Latest/)
	- View and download the AIM return xsd and wsdl from this current directory
	
- Returns Service 
	- [Download the build pack](../Service%20-%20Return/Latest/) to view data definitions of each operation and response status code definitions
	
- OAuth Authentication 
	- [How to Integrate with 0Auth](AIM_Auth_Access_Token_Steps.md)
	- [Sample curl commands - for testing the OAuth flow](AIM_Auth_Access_Token_Steps.md)

- Identity and Access Service 
	- [Download the build pack](../Service%20-%20Identity%20and%20Access/Latest/)for OAuth 2.0 implementation 

Features Details:
-----------------

- Test Scenarios
	[Test Scenarios](images/Emulated_Services_Coverage_Map-Return_AIM.png)

- Test Data
This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses. Text in italics represents the name of the XML node in the request.
	**To Add**
	
	Operation | Scenario ID | Data | 
	File | EMS_AIM0183 | Customer IRD (identifier): 123090918
	RetrieveFilingObligations | EMS_AIM042 | Customer IRD (identifier): 123064887 
	Prepop | EMS_AIM054 | Customer IRD (identifier): abcdefgh 
	Prepop | EMS_AIM063 | Customer IRD (identifier): 123064887 
	Prepop | EMS_AIM059 | Customer IRD (identifier): 123066081 
	RetrieveReturn | EMS_AIM028 | Customer IRD (identifier): 123081420 
	RetrieveStatus | EMS_AIM065 | Customer IRD (identifier): 123090918 periodEndDate: 2019-12-31 
	RetrieveStatus | EMS_AIM066 | Customer IRD (identifier): 123090918 periodEndDate: 2017-12-31 
	RetrieveStatus | EMS_AIM034 | Customer IRD (identifier): 123090918 (two-monthly even filer) periodEndDate: 2017-11-30 
	
        
- Message samples - simulating AIM Returns Operations:
    - PrePop
        - Positive response
            - [request sample](sample_messages/body-aim-returnprepop-request.xml)
            - [response sample](sample_messages/body-aim-returnprepop-response.xml)
    - File
        - Positive response
            - [request sample](sample_messages/body-aim-returnfile-request.xml)
            - [response sample](sample_messages/body-aim-returnfile-response.xml)
    - RetrieveStatus
        - Positive response
            - [request sample](sample_messages/body-aim-returnstatus-request.xml)
            - [response sample](sample_messages/body-aim-returnstatus-response.xml)
    - RetrieveFilingObligations
        - Positive response
            - [request sample](sample_messages/body-aim-filingobligation-request.xml)
            - [response sample](sample_messages/body-aim-filingobligation-response.xml)
    - RetrieveReturn
        - Positive response
            - [request sample](sample_messages/body-aim-retrievereturn-request.xml)
            - [response sample](sample_messages/body-aim-retrievereturn-response.xml)

            
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