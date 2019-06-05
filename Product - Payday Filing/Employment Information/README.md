![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Employment Information (EI) Returns Software Development Kit (SDK)

## Key Documentation:

- Business use cases
	- [view on IR website](https://www.classic.ird.govt.nz/resources/9/5/95275fd7-967a-4b87-877f-a8968807e45e/Payday+filing+-+Employment+Information+business+use+cases.pdf)
	
- Schemas and WSDLs
	- View and download the [common xsd](../../Schema%20-%20Common/)
	- View and download the [return service common xsd](../../Service%20-%20Return/Latest/)
	- View and download the Employment Income (EI) return [XSD](ReturnEI.v1.xsd) and [WSDL](ReturnsEIDevWsdl.wsdl) from this current directory
	
- Returns Service 
	- [Download the build pack](../../Service%20-%20Return/Latest/Gateway%20Services%20Build%20Pack%20-%20Return%20Service%20-%20EI.pdf) to view data definitions of each operation and response status code definitions

- Message Samples
    - [View Message samples for requests and positive responses](#message-samples)

- Find out about [Employee Details SDK, payday filing business rules and calculations](../)

## Environment Information: 

- [Mock Environment Information - Emulated Serices](#mock-environment-information)

- [Test Environment Information - Test Scenarios, mindmap and URL Endpoints](#test-environment-information)

- [Production Environment Information - URL Endpoints](#Production-Environment-Information)	

## Supporting Services:

* Service: Identity and Access – view [How to integrate, OAuth requests and responses message sample and build pack](../../Service%20-%20Identity%20and%20Access/Latest/) 
* Service: Intermediation [Service - Intermediation](../Service%20-%20Intermediation)	

## Message samples:
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

## Mock Environment Information:
-----------------

- Mock URL Endpoint
    - https://mock-ei.ird.digitalpartner.services/ 

- Test Scenarios
	- Employment Information Test Scenarios Mindmap
	
	![Test Scenarios](images/Employment_Information_Test_Scenarios_Mind_Map.png)

- Test Data
	- The following test data can be tested in our Mock Services environment when submitting requests to the service operations
	- This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses. 
	- Text in italics represents the name of the XML node in the request.
	
	
	|Operation | Scenario ID | Data|
	|--- | --- | ---|
	|Prepop | EMS_EI001 | Employer IRD (*identifier*): 123041607|
	| | | | *periodEndDate*: 2018-04-30|
	| | | | *payDayDate*: 2018-04-10|
	|Prepop | EMS_EI002 | Employer IRD (*identifier*): 123094018|
	| | | | *periodEndDate*: 2018-12-31|
	| | | | *payDayDate*: 2018-12-10|
	| RetrieveReturn | EMS_EI017 | Employer IRD (*identifier*): 123041607|
	| | | | *periodEndDate*: 2018-04-30|
	| | | | *payDayDate*: 2018-04-10|
	| | | | *submissionKey*: 987654321|
	RetrieveReturn | EMS_EI017 | Employer IRD (*identifier*): 123094018|
	| | | | *periodEndDate*: 2018-12-31|
	| | | | *payDayDate*: 2018-12-10|
	| | | | *submissionKey*: 987654321|


## Test Environment Information:
-----------------

* Test Scenarios
	- [Download test scenarios report template](Payday%20Filing%20–%20Employment%20Information%20-%20Test%20Report%20Template.docx)

* Test URL Endpoints
	- Cloud Gateway Service: https://test3.services.ird.govt.nz:4046/gateway/gws/returns/
	- Native Desktop Gateway Service: https://test3.services.ird.govt.nz/gateway2/gws/returns/
	- Cloud SOAP WSDL: https://test3.services.ird.govt.nz:4046/gateway/gws/returns/?wsdl
	- Native Desktop SOAP WSDL: https://test3.services.ird.govt.nz/gateway2/gws/returns/?wsdl
            
## Production Environment Information:
-----------------

* Production URL Endpoints
	- Cloud Gateway Service: https://services.ird.govt.nz:4046/gateway/gws/returns/
	- Native Desktop Gateway Service: https://services.ird.govt.nz/gateway2/gws/returns/
	- Cloud SOAP WSDL: https://services.ird.govt.nz:4046/gateway/gws/returns/?wsdl
	- Native Desktop SOAP WSDL https://services.ird.govt.nz/gateway2/gws/returns/?wsdl