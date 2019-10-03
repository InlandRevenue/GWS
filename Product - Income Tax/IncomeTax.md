![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# Income Tax Software Development Kit (SDK)

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
	
* [Income Tax Form Types](#Income-Tax-Form-Types) 

* [Sample request and responses](#Sample-request-and-responses)

---

## Primary income tax return: 

* IR3 - Resident Individual Income Tax Return
	* IR10 - Financial statements summary 
	* IR833 - Property sale information  
	* IR3F - arming income 
	* IR3B - Schedule of business income
	* IR3R - Rental income schedule
	* IR3K - Sale or disposal of financial arrangements
	* IR307 - Schedule of beneficiary’s estate or trust income
	* IR308 - Branch equivalent tax account return
	* IR215 - Adjust your income 
	* CFC - Controlled foreign investment
	
* IR3NR – Non-Resident Individual Income Tax Return
	* IR10 - Financial statements summary 
	* IR833 - Property sale information  
	* IR3F - arming income 
	* IR3B - Schedule of business income
	* IR3R - Rental income schedule
	* IR3K - Sale or disposal of financial arrangements
	
* IR4/S - Companies Income Tax Return  
	* IR10 - Financial statements summary
	* IR833 - Property sale information  
	* IR44E - Group investment fund return 
	* IR4J - Annual imputation return  
	* CFC - Controlled foreign investment  

* IR6 - Estate or Trust Income Tax Return
	* IR10 - Financial statements summary  
	* IR833 - Property sale information  
	* IR3F - Farming income 
	* IR3B - Schedule of business income 
	* IR3R - Rental income schedule 
	* IR44E - Group investment fund return 
	* IR308 - Branch equivalent tax account return 
	* CFC - Controlled foreign investment
	
* IR7 - Partnership and LTCs income tax return 
	* IR10 - Financial statements summary
	* IR833 - Property sale information 
	* IR3F - Farming income 
	* IR3B - Schedule of business income 
	* IR3R - Rental income schedule
	* IR44E - Group investment fund return
	* CFC - Controlled foreign investment
	
* IR8 - Māori authorities income tax return 
	* IR10 - Financial statements summary 
	* IR833 - Property sale information  
	* IR3B - Schedule of business income
	* IR3R - Rental income schedule
	* IR8J - Property sale information 
	* CFC - Controlled foreign investment 
	
* IR8J - Māori authorities credit account return 
	* IR10 - Financial statements summary  
	* IR833 - Property sale information  
	* IR3B - Schedule of business income 
	* IR3R - Rental income schedule 
	* IR8J - Property sale information  
	* CFC - Controlled foreign investment 

* IR9 - Clubs or societies income tax return 
	* IR10 - Financial statements summary  
	* IR833 - Property sale information  
	* CFC - Controlled foreign investment 
	
* IR44 - Superannuation funds income tax return
	* IR10 - Financial statements summary
	* IR833 - Property sale information 
	* CFC  - Controlled foreign investment
	
* IR215 - Adjust your income 
	* Does not support attachments	
	
## Attachment income tax return:	

* IR3F - Farming income
* IR3B - Schedule of business income
* IR3R - Rental income schedule
* IR3K - Sale or disposal of financial arrangements 
* IR4J - Annual imputation return 
* IR44E - Group investment fund return
* IR10 - Financial statements summary 
* IR215 - Adjust your income
* IR307 - Schedule of beneficiary’s estate or trust income
* IR833 - Property sale information
* IR308 - Branch equivalent tax account return  
* CFC - Controlled foreign investment  
* PTS - Individual income tax return   

> Note: PTS Individual income tax return RetrieveReturn and RetrieveStatus for income years prior to 2019 


## Sample request and responses

- File
    - [IR3 File request (with all applicable attachments)](sample%20messages/file_request_ir3_all_attachments.xml)
    - [IR3NR File request](sample%20messages/file_request_ir3nr_standalone.xml)
    - [IR4 File request (with all applicable attachments)](sample%20messages/file_request_ir4_all_attachments.xml)
    - [IR4J File request](sample%20messages/file_request_ir4j_standalone.xml)
    - [IR6 File request](sample%20messages/file_request_ir6_standalone.xml)
    - [IR7L File request](sample%20messages/file_request_ir7l_standalone.xml)
    - [IR7P File request](sample%20messages/file_request_ir7p_standalone.xml)
    - [IR8 File request](sample%20messages/file_request_ir8_standalone.xml)
    - [IR8J File request](sample%20messages/file_request_ir8j_standalone.xml)
    - [IR9 File request](sample%20messages/file_request_ir9_standalone.xml)
    - [IR44 File request](sample%20messages/file_request_ir44_standalone.xml)
    - [File Response](sample%20messages/file_response.xml)
- RetrieveReturn
    - [RetrieveReturn request](sample%20messages/retrievereturn_request.xml)
    - [IR3 RetrieveReturn response](sample%20messages/retrievereturn_response_ir3.xml)
    - [IR3NR RetrieveReturn response](sample%20messages/retrievereturn_response_ir3nr.xml)
    - [IR4 RetrieveReturn response](sample%20messages/retrievereturn_response_ir4.xml)
    - [IR4J RetrieveReturn response](sample%20messages/retrievereturn_response_ir4j.xml)
    - [IR6 RetrieveReturn response](sample%20messages/retrievereturn_response_ir6.xml)
    - [IR7L RetrieveReturn response](sample%20messages/retrievereturn_response_ir7l.xml)
    - [IR7P RetrieveReturn response](sample%20messages/retrievereturn_response_ir7p.xml)
    - [IR8 RetrieveReturn response](sample%20messages/retrievereturn_response_ir8.xml)
    - [IR8J RetrieveReturn response](sample%20messages/retrievereturn_response_ir8j.xml)
    - [IR9 RetrieveReturn response](sample%20messages/retrievereturn_response_ir9.xml)
    - [IR44 RetrieveReturn response](sample%20messages/retrievereturn_response_ir44.xml)
- RetrieveReturn
    - [RetrieveStatus request](sample%20messages/retrievestatus_request.xml)
    - [RetrieveStatus response](sample%20messages/retrievestatus_response.xml)
- Prepop
    - [Prepop request](sample%20messages/prepop_request.xml)
    - [Prepop response (Individual customer)](sample%20messages/prepop_response_individual.xml)
    - [Prepop response (Non-Individual customer)](sample%20messages/prepop_response_nonindividual.xml)
- RetrieveFilingObligations
    - [RetrieveFilingObligations request](sample%20messages/retrievefilingobligations_request.xml)
    - [RetrieveFilingObligations response](sample%20messages/retrievefilingobligations_response.xml)
	
	
## Environment Information: 
- [Mock Environment Information - Emulated Services, Mindmap and Test data](test%20details/TestingInfomation.md#mock-environment-information)
- [Test Environment Information - Test Scenarios Report Template, Mindmap and URL Endpoints](test%20details/TestingInfomation.md#test-environment-information)
- [Production Environment Information - URL Endpoints](test%20details/TestingInfomation.md#Production-Environment-Information)		