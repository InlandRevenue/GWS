![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

Employee Details (ED) Software Development Kit (SDK)
=======================================

Key Features:
-------------

- Simulating Employee Details (ED) filing operations
	- [Test scenarios report template, mindmap and data](#test-details)
    - [Message samples](#message-samples-) - positive responses
	
- Business use cases
	- [view on IR website](https://www.ird.govt.nz/resources/e/2/e2d9e606-76d3-44f7-9127-2584666b5f09/Payday+filing+-+Employee+details+business+use+cases.pdf)
	
- Schemas and WSDLs
	- View and download the [common xsd](../../Schema%20-%20Common/)
	- View and download the [return service common xsd](../../Service%20-%20Return/Latest/)
	- View and download the Employee Details (ED) [XSD](Employment.xsd) and [WSDL](EmploymentDevWsdl.wsdl) from this current directory
	
- Employment Service 
	- [Download the build pack](Gateway%20Services%20Build%20Pack%20-%20Employment%20Service.pdf) to view data definitions of each operation and response status code definitions
	
- Identity and Access Service
	- [How to Integrate with OAuth](../../Service%20-%20Identity%20and%20Access/Latest/OAuth%20Authentication%20-%20How%20to%20Integrate.md)
	- [Message Samples](../../Service%20-%20Identity%20and%20Access/Latest/) - OAuth requests and responses
	- [Download the build pack](../../Service%20-%20Identity%20and%20Access/Latest/Build%20pack%20-%20Identity%20and%20Access%20Services.pdf) - for OAuth 2.0 implementation

- Find out about [Employee Information SDK, payday filing business rules and calculations](../)

Supporting Services
-------------
* [Service - Intermediation](../Service%20-%20Intermediation)

Test Details:
-----------------

- Test Scenarios 
	- [Download the test scenarios report template](Payday%20Filing%20–%20Employee%20Details%20-%20Test%20Report%20Template.docx)
	- Employee Details Test Scenarios Mindmap
	
	![Test Scenarios](images/Employee_Details_Test_Scenarios_Mind_Map.png)

- Test Data
	- The following test data can be tested in our Mock Services environment when submitting requests to the service operations
	- This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses. 
	- Text in italics represents the name of the XML node in the request.
	-
	
	Operation | Scenario ID | Data
	--- | --- | ---
	RetrieveList | EMS_ES081 | Employee IRD (*identifier*): 123114116
	Update | EMS_ES096 | Employee IRD (*identifier*): 123183711
	Create | EMS_ES095 | Employee IRD (*identifier*): 123183711
	Update | EMS_ES099 | employmentStartDate: today's date
        
Message samples :
----------------- 
- Simulating Employment Service Operations:
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

- Mock URL Endpoint
    - https://mock-intermediation.ird.digitalpartner.services/

- Test URL Endpoint
    - Cloud Gateway Service: https://test3.services.ird.govt.nz:4046/gateway/gws/returns/
    - Native Desktop Gateway Service: https://test3.services.ird.govt.nz/gateway2/gws/returns/
            
- Production URL Endpoint
    - Cloud Gateway Service: https://services.ird.govt.nz:4046/gateway/gws/returns/
    - Native Desktop Gateway Service: https://services.ird.govt.nz/gateway2/gws/returns/