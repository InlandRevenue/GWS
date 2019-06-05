![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# GST Returns Software Development Kit (SDK)

## Key Documentation:

- Business use cases
	- [view on IR website](https://www.classic.ird.govt.nz/resources/8/9/89938b0d-09d4-49c9-8e4b-ad30527a9d56/GST+Business+use+cases.pdf)
	
- Schemas and WSDLs
	- View and download the [common xsd](../Schema%20-%20Common/)
	- View and download the [return service common xsd](../Service%20-%20Return/Latest/)
	- View and download the GST return [XSD](ReturnGST.v1.xsd) and [WSDL](ReturnsGSTDevWsdl.v1.wsdl) from this current directory

- Returns Service 
	- [Download the Return Service GST build pack](../Service%20-%20Return/Latest/Gateway%20Services%20Build%20Pack%20-%20Return%20Service%20-%20GST.pdf) to view data definitions of each operation and response status code definitions

- Message Samples
    - [View Message samples for requests and positive responses](#message-samples)
	
## Environment Information: 

- [Mock Environment Information - Emulated Services, Mindmap and Test data](#mock-environment-information)
	
- [Test Environment Information - Test Scenarios Report Template, Mindmap and URL Endpoints](#test-environment-information)

- [Production Environment Information - URL Endpoints](#Production-Environment-Information)	

## Supporting Services:

* Service: Identity and Access – view [How to integrate, OAuth requests and responses message sample and build pack](../Service%20-%20Identity%20and%20Access/Latest/) 
* Service: Intermediation – view [Schemas, WSDLs, and build pack](../Service%20-%20Intermediation/)

## Message Samples:
-----------------

* Simulating GST Returns Operations:
    - PrePop
        - Positive response
            - [request sample](sample%20messages/body-gst-returnprepop-request.xml)
            - [response sample](sample%20messages/body-gst-returnprepop-response.xml)
    - File
        - Positive response
            - [request sample](sample%20messages/body-gst-returnfile-request.xml)
            - [response sample](sample%20messages/body-gst-returnfile-response.xml)
    - RetrieveStatus
        - Positive response
            - [request sample](sample%20messages/body-gst-returnstatus-request.xml)
            - [response sample](sample%20messages/body-gst-returnstatus-response.xml)
    - RetrieveFilingObligations
        - Positive response
            - [request sample](sample%20messages/body-gst-filingobligation-request.xml)
            - [response sample](sample%20messages/body-gst-filingobligation-response.xml)
    - RetrieveReturn
        - Positive response
            - [request sample](sample%20messages/body-gst-retrievereturn-request.xml)
            - [response sample](sample%20messages/body-gst-retrievereturn-response.xml)

## Mock Environment Information:
-----------------

* Mock Emulated Services URL
	* https://mock-gst.ird.digitalpartner.services

* Test Scenarios 
	- GST Test Scenarios Mindmap
	
	![Test Scenarios](images/Emulated_Services_Coverage_Map-Return_GST.png)

* Test Data
	- The following test data can be tested in our Mock Services environment when submitting requests to the service operations
	- This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses. 
	- Text in italics represents the name of the XML node in the request.
	
	    
	|Operation | Scenario ID | Data|
	|-|-|-|
	|File | EMS_GST013 | Customer IRD (*identifier*): 123090918|
	|File | EMS_GST012 | Customer IRD (*identifier*): 123039456|
	|Prepop | EMS_GST027 | Customer IRD (*identifier*): 123039858 |
	|Prepop | EMS_GST028 | Customer IRD (*identifier*): 123084226 |
	|Prepop | EMS_GST029 | Customer IRD (*identifier*): 123084217|
	|Prepop | EMS_GST030 | Customer IRD (*identifier*): 123088077|
	|Prepop | EMS_GST031 | Customer IRD (*identifier*): 123070054 |
	|Prepop | EMS_GST032 | Customer IRD (*identifier*): 123101294|
	|Prepop | EMS_GST033 | Customer IRD (*identifier*): 123084225 |
    |Prepop | EMS_GST034 | Customer IRD (*identifier*): 123080106 |
        
## Test Environment Information:
-----------------

* Test Scenarios
	- [Download test scenarios report template](GST%20-%20Return%20Service%20-%20Test%20Report%20Template.docx)

* Test Environment URL Endpoints
	
	* Cloud Gateway Service: https://test3.services.ird.govt.nz:4046/gateway/gws/returns/
	* Native Desktop Gateway Service: https://test3.services.ird.govt.nz/gateway2/gws/returns/
	* Cloud SOAP WSDL: https://test3.services.ird.govt.nz:4046/gateway/gws/returns/?wsdl
	* Native Desktop SOAP WSDL: https://test3.services.ird.govt.nz/gateway2/gws/returns/?wsdl
            
## Production Environment Information:
-----------------

* Production URL Endpoints

	- Cloud Gateway Service: https://services.ird.govt.nz:4046/gateway/gws/returns/
	- Native Desktop Gateway Service: https://services.ird.govt.nz/gateway2/gws/returns/
	- (Cloud) SOAP WSDL: https://services.ird.govt.nz:4046/gateway/gws/returns/?wsdl
	- (Native Desktop) SOAP WSDL: https://services.ird.govt.nz/gateway2/gws/returns/?wsdl