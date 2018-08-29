![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

AIM Returns Software Development Kit (SDK)
=======================================

Key Features:
-------------

- Simulating AIM filing operations
	- [Test Scenarios and data](#test-details)
    - [Message samples](#message-samples-) - positive responses
	- [Requests Matching Logic](#requests-matching-logic)
	
- Schemas and WSDLS
	- View and download the [common xsd](../Schema%20-%20Common/)
	- View and download the [return service common xsd](../Service%20-%20Return/Latest/)
	- View and download the AIM return [xsd](ReturnAIM.v1.xsd) and [wsdl](ReturnsAIMDevWsdl.wsdl) from this current directory
	
- Returns Service 
	- [Download the build pack](../Service%20-%20Return/Latest/Gateway%20Services%20Build%20Pack%20-%20Return%20Service.pdf) to view data definitions of each operation and response status code definitions
	
- Identity and Access Service
	- [How to Integrate with OAuth](../Service%20-%20Identity%20and%20Access/Latest/OAuth%20Authentication%20-%20How%20to%20Integrate.md)
	- [Sample curl commands](../Service%20-%20Identity%20and%20Access/Latest/OAuth%20Authentication%20-%20How%20to%20Integrate.md) - for testing the OAuth flow
	- [Message Samples](../Service%20-%20Identity%20and%20Access/Latest/) - OAuth requests and responses
	- [Download the build pack](../Service%20-%20Identity%20and%20Access/Latest/Build%20pack%20-%20Identity%20and%20Access%20Services.pdf) - for OAuth 2.0 implementation   

Test Details:
-----------------

- Test Scenarios
	- [Download test scenarios template](AIM%20-%20Returns%20Service%20-%20Test%20Scenarios.docx)
	![Test Scenarios](images/Emulated_Services_Coverage_Map-Return_AIM.png)

- Test Data
	- The following test data can be tested in our Mock Services environment when submitting requests to the service operations
	- This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses. 
	- Text in italics represents the name of the XML node in the request.
	-
	
	Operation | Scenario ID | Data
	--- | --- | ---
	File | EMS_AIM0183 | Customer IRD (*identifier*): 123090918
	RetrieveFilingObligations | EMS_AIM042 | Customer IRD (*identifier*): 123064887 
	Prepop | EMS_AIM054 | Customer IRD (*identifier*): abcdefgh 
	Prepop | EMS_AIM063 | Customer IRD (*identifier*): 123064887 
	Prepop | EMS_AIM059 | Customer IRD (*identifier*): 123066081 
	RetrieveReturn | EMS_AIM028 | Customer IRD (*identifier*): 123081420 
	RetrieveStatus | EMS_AIM065 | Customer IRD (*identifier*): 123090918 
	 | | | *periodEndDate*: 2019-12-31 
	RetrieveStatus | EMS_AIM066 | Customer IRD (*identifier*): 123090918
	 | | | *periodEndDate*: 2017-12-31 
	RetrieveStatus | EMS_AIM034 | Customer IRD (*identifier*): 123090918 (two-monthly even filer)
	 | | | *periodEndDate*: 2017-11-30 
        
Message samples :
-----------------

- Simulating AIM Returns Operations:
    - PrePop
        - Positive response
            - [request sample](sample%20messages/body-aim-returnprepop-request.xml)
            - [response sample](sample%20messages/body-aim-returnprepop-response.xml)
    - File
        - Positive response
            - [request sample](sample%20messages/body-aim-returnfile-request.xml)
            - [response sample](sample%20messages/body-aim-returnfile-response.xml)
    - RetrieveStatus
        - Positive response
            - [request sample](sample%20messages/body-aim-returnstatus-request.xml)
            - [response sample](sample%20messages/body-aim-returnstatus-response.xml)
    - RetrieveFilingObligations
        - Positive response
            - [request sample](sample%20messages/body-aim-filingobligation-request.xml)
            - [response sample](sample%20messages/body-aim-filingobligation-response.xml)
    - RetrieveReturn
        - Positive response
            - [request sample](sample%20messages/body-aim-retrievereturn-request.xml)
            - [response sample](sample%20messages/body-aim-retrievereturn-response.xml)

            
Requests Matching Logic
-----------------------

- ReadMe Page - (default) port 8080 of root path of Welcome Page
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