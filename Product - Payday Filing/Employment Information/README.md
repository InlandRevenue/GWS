![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

Employment Information (EI) Returns Software Development Kit (SDK)
=======================================

Key Features:
-------------

- Simulating Employment Information (EI) filing operations
	- [Test Scenarios and data](#test-details)
    - [Message samples](#message-samples-) - positive responses
	- [Requests Matching Logic](#requests-matching-logic)
	
- Schemas and WSDLS
	- View and download the [common xsd](../../Schema%20-%20Common/)
	- View and download the [return service common xsd](../../Service%20-%20Return/Latest/)
	- View and download the Employment Income (EI) return [xsd](ReturnEI.v1.xsd) and [wsdl](ReturnsEIDevWsdl.wsdl) from this current directory
	
- Returns Service 
	- [Download the build pack](../../Service%20-%20Return/Latest/Gateway%20Services%20Build%20Pack%20-%20Return%20Service.pdf) to view data definitions of each operation and response status code definitions
	
- Identity and Access Service
	- [How to Integrate with OAuth](../../Service%20-%20Identity%20and%20Access/Latest/OAuth%20Authentication%20-%20How%20to%20Integrate.md)
	- [Sample curl commands](../../Service%20-%20Identity%20and%20Access/Latest/OAuth%20Authentication%20-%20How%20to%20Integrate.md) - for testing the OAuth flow
	- [Message Samples](../../Service%20-%20Identity%20and%20Access/Latest/) - OAuth requests and responses
	- [Download the build pack](../../Service%20-%20Identity%20and%20Access/Latest/Build%20pack%20-%20Identity%20and%20Access%20Services.pdf) - for OAuth 2.0 implementation   

Test Details:
-----------------

- Test Scenarios 
	- [Download test scenarios template](Payday%20Filing%20–%20Employment%20Information%20Test%20Scenarios.docx)
	![Test Scenarios](images/Emulated_Services_Coverage_Map-Return_EI.png)

- Test Data
	- The following test data can be tested in our Mock Services environment when submitting requests to the service operations
	- This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses. 
	- Text in italics represents the name of the XML node in the request.
	-
	
	Operation | Scenario ID | Data
	--- | --- | ---
	Prepop | EMS_EI001 | Employer IRD (*identifier*): 123041607
	 | | | *periodEndDate*: 2018-04-30
	 | | | *payDayDate*: 2018-04-10
	Prepop | EMS_EI002 | Employer IRD (*identifier*): 123094018
	 | | | *periodEndDate*: 2018-12-31
	 | | | *payDayDate*: 2018-12-10
	RetrieveReturn | EMS_EI017 | Employer IRD (*identifier*): 123041607
	 | | | *periodEndDate*: 2018-04-30
	 | | | *payDayDate*: 2018-04-10
	 | | | *submissionKey*: 987654321
	RetrieveReturn | EMS_EI017 | Employer IRD (*identifier*): 123094018
	 | | | *periodEndDate*: 2018-12-31
	 | | | *payDayDate*: 2018-12-10
	 | | | *submissionKey*: 987654321
        
Message samples :
-----------------

- Simulating EI Returns Operations:
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