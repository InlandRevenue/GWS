![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Resident withholding tax (RWT) Software Development Kit (SDK) for Investment Income Reporting

## Key Documentation:

- Business use cases
	- [Download and view](III%20-%20RWT%20-%20GWS%20business%20use%20cases.pdf)
	
- Schemas and WSDLs
	- View and download the [common v2 xsd](../../Schema%20-%20Common/Common.v2.xsd)
	- View and download the [Return Service common v2 xsd](../Service%20-%20Return%20III/Latest/)
	- View and download the RWT return [XSD](ReturnRWT.v1.xsd) and [WSDL](RWTDevWsdl.wsdl) from this current directory
	
- Returns Service - Investment Income Information 
	- [Download the build pack](../Service%20-%20Return%20III/Latest/Gateway%20Services%20Build%20Pack%20-%20Return%20Service%20-%20III.pdf) to view data definitions of each operation and response status code definitions

## Sample Message:

* File
	* Income Type DIVINT
		* [Request](sample%20messages/RWT_File_Request_incomeType_DIVINT.xml)   
		* [Response](sample%20messages/RWT_File_Response_incomeType_DIVINT.xml)
		
	* Income Type MAORI
		* [Request](sample%20messages/RWT_File_Request_incomeType_MAORI.xml)
		* [Response](sample%20messages/RWT_File_Response_incomeType_MAORI.xml)		
	
	* Multiple Income Information
		* [Request](sample%20messages/RWT_File_Request_with_multiple_income_information.xml)
		* [Response](sample%20messages/RWT_File_Response_with_multiple_income_information.xml)	
		
	* Multiple Joint Account Holders
		* [Request](sample%20messages/RWT_File_Request_with_multiple_joint_account_holders.xml)
		* [Response](sample%20messages/RWT_File_Response_with_multiple_joint_account_holders.xml)	
	
* File Amendment
	* [File Amendment](sample%20messages/RWT_File_Request_amendment.xml)
	
	* Request Amendment by Reference Id
		* [Request](sample%20messages/RWT_File_Request_amendment_by_referenceId.xml)
		* [Response](sample%20messages/RWT_File_Response_amendment_by_referenceId.xml)
		
* RetrieveReturn
	* Retrieve Return with submission 	
		* [Request](sample%20messages/RWT_RetrieveReturn_Request_with_submission_key.xml)
		* [Response](sample%20messages/RWT_RetrieveReturn_Response_with_submission_key.xml)
	* Retrieve Return without submission 	
		* [Request](sample%20messages/RWT_RetrieveReturn_Request_without_submission_key.xml)
		* [Response](sample%20messages/RWT_RetrieveReturn_Response_without_submission_key.xml)
		
* ReturnSatus	
	* With submission Key
		* [Request](sample%20messages/RWT_ReturnSatus_Request_without_submission_key.xml)
		* [Response](sample%20messages/RWT_ReturnSatus_Request_with_submission_key.xml)
	* Without submission Key
		* [Request](sample%20messages/RWT_ReturnSatus_Response_without_submission_key.xml)
		* [Response](sample%20messages/RWT_ReturnSatus_Response_with_submission_key.xml)

---
	
## Environment Information:


	
- Mock Environment Information
	- [Mindmap and test data](../Test%20Details%20-%20IIR/README.md#mock-environment-information)
	- [Mock URL Endpoints](../Test%20Details%20-%20IIR/README.md#mock-environment)

- Test Environment Information
	- [Test scenarios report template and mindmap](../Test%20Details%20-%20IIR/README.md#test-environment-information)
	- [Test URL Endpoints](../Test%20Details%20-%20IIR/README.md#test-environment-information)

- Production Environment Information
	- [Production URL Endpoints](../Test%20Details%20-%20IIR/README.md#production-environment-information)	 
	
## Supporting Services: 

* Service - Identity and Access – view [How to integrate, OAuth requests and responses message sample and build pack](../../Service%20-%20Identity%20and%20Access/Latest/)
