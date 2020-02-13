![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# AIM Returns Software Development Kit (SDK)

#### Release version 1.0

## New Features:

* Changed to meet new legislation around mid-year entry. 
* File/prepop now 
	* allows for mid-year entry.
	* returns penalties or interest applied to the customer period. 
* File has 3 new elements to declare:
	* If the company is now earning over $5M 
	* If the company is deciding to enter AIM mid-year 
	* Declare any shareholders that the AIM company is paying provisional tax for.

## Key Documentation:

- Business use cases and worked examples
	- [view on IR website](https://www.classic.ird.govt.nz/resources/5/0/50d56274-2a12-46ac-a9e3-a4a84d3f47bc/aim-business-use-cases-worked-examples.pdf)
	
- Schemas and WSDLs
	- View and download the [common v2 xsd](../Schema%20-%20Common/)
	- View and download the [return service common v2 xsd](../Service%20-%20Return/Latest/)
	- View and download the AIM return [XSD](ReturnAIM.v2.xsd) and [WSDL](ReturnsAIMDevWsdl.v2.wsdl) from this current directory
	
- Return Service 
	- [Download the Return Service AIM v2.0 build pack](../Service%20-%20Return/Latest/Gateway%20Services%20Build%20Pack%20-%20Return%20Service%20-%20AIM%20-%20V2.0.pdf) to view data definitions of each operation and response status code definitions

- Message Samples
    - [View Message samples for requests and positive responses](#message-samples)		
	
## Environment Information: 

- [Mock Environment Information - Emulated Services, Mindmap and Test data](#mock-environment-information)
	
- [Test Environment Information - Test Scenarios Report Template, Mindmap and URL Endpoints](#test-environment-information)

- [Production Environment Information - URL Endpoints](#Production-Environment-Information)	
	
## Supporting services

* Service: Identity and Access – view [How to integrate, OAuth requests and responses message sample and build pack](../Service%20-%20Identity%20and%20Access/Latest/) 
* Service: Intermediation – view [Schemas, WSDLs, and build pack](../Service%20-%20Intermediation/)

## Message samples:
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

## Mock Environment Information:
-----------------

* Mock Emulated Services URL
	* https://mock-aim.ird.digitalpartner.services

- AIM Mock Scenarios Mindmap
	- [View larger image](images/AIM_Mock_Scenarios_Mindmap.png)
	![Mock Scenarios](images/AIM_Mock_Scenarios_Mindmap.png) 

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

## Test Environment Information:
-----------------

* Test Scenarios
	- [Download test scenarios report template](AIM%20-%20Return%20Sevice%20-%20Test%20Report%20Template.docx)
	- AIM Test Scenarios Mindmap - [view larger image](images/AIM_v2_Test_Scenarios_Mindmap.png)
	![Test Scenarios](images/AIM_v2_Test_Scenarios_Mindmap.png)

* Test URL Endpoint
	* Cloud Gateway Service: https://test3.services.ird.govt.nz:4046/gateway/gws/returns/
	* Native Desktop Gateway Service: https://test3.services.ird.govt.nz/gateway2/gws/returns/

## Production Environment Information:
-----------------

* Production URL Endpoints

	- Cloud Gateway Service: https://services.ird.govt.nz:4046/gateway/gws/returns/
	- Native Desktop Gateway Service: https://services.ird.govt.nz/gateway2/gws/returns/
	- (Cloud) SOAP WSDL: https://services.ird.govt.nz:4046/gateway/gws/returns/?wsdl
	- (Native Desktop) SOAP WSDL: https://services.ird.govt.nz/gateway2/gws/returns/?wsdl