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
	
* [Income profile types and related forms](#Income-profile-types-and-related-forms)

* [Income Tax Form Types](#Income-Tax-Form-Types) 

* [Sample request and responses](#Sample-request-and-responses)

---

## Income profile types and related forms:  

| Income profile type | Forms |
| --- | --- |
| NZ income with tax deducted | Individual income tax return - **IR3** _Prepop_ <br/> Non-resident income tax return - **IR3NR** |
| Schedula Payments  | Individual income tax return - **IR3** _Prepop_ <br/> Companies income tax return - **IR4** <br/> Partnership and LTCs income tax return - **IR7**|
| Investment income  | Individual income tax return - **IR3** _Prepop_ <br/> Non-resident income tax return - **IR3NR** |
| Other expenses | Individual income tax return - **IR3** _Prepop_ |
| Net losses brought forward |   Individual income tax return - **IR3** _Prepop_ <br/> Non-resident income tax return - **IR3NR**|
| Excess imputation credits | Individual income tax return - **IR3** _Prepop_ |
| NZ income with tax deducted  | Individual income tax return - **IR3** _Prepop_ |
| NZ interest  | Companies income tax return - **IR4** <br/> Estate or trust income tax return - **IR6** <br/> Partnership and LTCs income tax return - **IR7** <br/> Māori authorities income tax return - **IR8** <br/> Clubs or societies income tax return - **IR9**| 
| NZ dividends |Companies income tax return - **IR4**<br/>Estate or trust income tax return - **IR6**<br/>Māori authorities income tax return - **IR8**<br/> |
| Income from partnership, estate or trust  |Companies income tax return - **IR4**<br/> Estate or trust income tax return - **IR6**|
| Losses brought from previous years | Companies income tax return - **IR4** <br/> Estate or trust income tax return - **IR6** <br/> Māori authorities income tax return - **IR8** <br/> Clubs or societies income tax return - **IR9** |
| PIE | Companies income tax return - **IR4** <br/> Partnership and LTCs income tax return - **IR7**|
| Income from a look through company | Estate or trust income tax return - **IR6** <br/> Partnership and LTCs income tax return - **IR7**|
| Income from another partnership | Partnership and LTCs income tax return - **IR7**|
| Excess imputation credits brought forward | Clubs or societies income tax return - **IR9**|

## Primary Income Tax Form Types:

* Individual income tax return - IR3
	* Financial statements summary - IR10
	* Property sale information - IR833
	* Farming income - IR3F
	* Schedule of business income - IR3B
	* Rental income schedule - IR3R
	* Sale or disposal of financial arrangements - IR3K
	* Schedule of beneficiary’s estate or trust income - IR307
	* Branch equivalent tax account return - IR308
	* Adjust your income - IR215
	* Controlled foreign investment - CFC
* Companies income tax return - IR4
	* Financial statements summary - IR10 
	* Property sale information - IR833
	* Group investment fund return - IR44E
	* Annual imputation return - IR4J
	* Controlled foreign investment - CFC
* Annual imputation return - IR4J 
* Estate or trust income tax return - IR6 
	* Financial statements summary -IR10
	* Property sale information - IR833
	* Farming income - IR3F
	* Schedule of business income - IR3B
	* Rental income schedule - IR3R
	* Group investment fund return - IR44E
	* Branch equivalent tax account return -IR308
	* Controlled foreign investment - CFC
* Partnership and LTCs income tax return - IR7
	* Financial statements summary- IR10
	* Property sale information - IR833
	* Schedule of business income - IR3B
	* Rental income schedule - IR3R
	* Controlled foreign investment - CFC
* Māori authorities income tax return - IR8
	* Financial statements summary - IR10
	* Property sale information - IR833
	* Schedule of business income - IR3B
	* Rental income schedule - IR3R
	* Property sale information - IR8J
	* Controlled foreign investment - CFC
* Māori authorities credit account return - IR8J

* Clubs or societies income tax return - IR9
	* Financial statements summary - IR10
	* Property sale information - IR833
	* Controlled foreign investment - CFC
* Superannuation funds income tax return - IR44
	* Financial statements summary - IR10
	* Property sale information - IR833
	* Controlled foreign investment - CFC
	
## Attachment income tax return:	
* Annual imputation return - IR4J 
* Group investment fund return - IR44E
* Farming income - IR3F
* Schedule of business income - IR3B
* Rental income schedule - IR3R
* Sale or disposal of financial arrangements - IR3K 
* Financial statements summary - IR10
* Adjust your income - IR215
* Schedule of beneficiary’s estate or trust income - IR307
* Property sale information - IR833
* Branch equivalent tax account return - IR308 
* Controlled foreign investment - CFC
* Individual income tax return - PTS  

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