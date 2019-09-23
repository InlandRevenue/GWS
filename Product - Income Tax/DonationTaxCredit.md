![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# Donation Tax Credit Software Development Kit (SDK)

## Key Documentation:

* Business use cases
	* [view on IR website](https://www.classic.ird.govt.nz/software-providers/docs/)

* XSD Schemas 
    * View and download the [Income Return Common xsd](xsd/IncomeReturnCommon.v1.xsd) from this [xsd](xsd/) directory	
    * View the Income Tax XSD schema files from the [xsd](xsd/) directory
    * View and download the [return service common xsd](../Service%20-%20Return/Latest/)
    * View and download the [common xsd](../Schema%20-%20Common/)
	
* Returns Service 
	* Download and view the [Return Service Income Tax build pack](Gateway%20Services%20Build%20Pack%20-%20Return%20Service%20-%20INC.pdf) to view data definitions of each operation and response status code definitions		

* XSD Schemas 
    * View the Income Tax XSD schema files from the [xsd](xsd/) directory
    * View and download the [return service common v2 xsd](../Service%20-%20Return/Latest/)
    * View and download the [common v2 xsd](../Schema%20-%20Common/)

* [Sample request and responses](#Sample-request-and-responses)

---

## Sample request and responses

- File
    - [IR526 File request](sample%20messages/file_request_ir526_standalone.xml)
    - [File Response](sample%20messages/file_response.xml)
- RetrieveReturn
    - [IR526 RetrieveReturn request](sample%20messages/retrievereturn_request_ir526.xml)
    - [IR526 RetrieveReturn response](sample%20messages/retrievereturn_response_ir526.xml) 
- RetrieveReturn
    - [IR526 RetrieveStatus request](sample%20messages/retrievestatus_request_ir526.xml)
    - [IR526 RetrieveStatus response](sample%20messages/retrievestatus_response_ir526.xml)
   
## Environment Information: 
- [Mock Environment Information - Emulated Services, Mindmap and Test data](test%20details/TestingInfomation.md#mock-environment-information)
- [Test Environment Information - Test Scenarios Report Template, Mindmap and URL Endpoints](test%20details/TestingInfomation.md#test-environment-information)
- [Production Environment Information - URL Endpoints](test%20details/TestingInfomation.md#Production-Environment-Information)	