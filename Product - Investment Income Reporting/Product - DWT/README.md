![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Dividend withholding tax (DWT) Software Development Kit (SDK) for Investment Income Reporting

## Key Documentation:

* Business use cases
	* [Download and view](III%20-%20DWT%20-%20GWS%20business%20use%20cases.pdf)
	
* Schemas and WSDLs
	* View and download the [common v2 xsd](../../Schema%20-%20Common/Common.v2.xsd)
	* View and download the [Return Service common v2 xsd](../Service%20-%20Return%20III/Latest/)
	* View and download the DWT return [XSD](ReturnDWT.v1.xsd) and [WSDL](DWTDevWsdl.wsdl) from this current directory
	
- Return Service - Investment Income Reporting
	- [Download the build pack](../Service%20-%20Return%20III/Latest/Gateway%20Services%20Build%20Pack%20-%20Return%20Service%20-%20III.pdf) to view data definitions of each operation and response status code definitions
	
- Message Samples
    - [View Message samples for requests and positive responses](#message-samples)
	
## Environment Information:

- Mock Environment Information
	- [Mindmap and test data](../Test%20Details%20-%20IIR/README.md#mock-environment-information)
	- [Mock URL Endpoints](../Test%20Details%20-%20IIR/README.md#mock-environment)

- Test Environment Information
	- [Test scenarios report template and mindmap](../Test%20Details%20-%20IIR/README.md#test-environment-information)
	- [Test URL Endpoints](../Test%20Details%20-%20IIR/README.md#test-environment-information)

- Production Environment Information
	- [Production URL Endpoints](../Test%20Details%20-%20IIR/README.md#production-environment-information)	 

## Supporting services:

- Service - Identity and Access – view [how to integrate, OAuth requests and responses message sample and build pack](../Service%20-%20Return%20III/Latest/)

## Message Samples:
-----------------

- Simulating DWT Returns Operations:
    - File
		- [request sample](sample%20messages/DWTFileRequest.xml)
        - [positive response sample](sample%20messages/DWTFileResponse.xml)
	- File Amendment
		- [request sample by period end date](sample%20messages/DWTFileRequestUpdate_PeriodEndDate.xml)
		- [request sample by submission key](sample%20messages/DWTFileRequestUpdate_SubmissionKey.xml)
        - [positive response sample](sample%20messages/DWTFileResponse.xml)
    - RetrieveStatus
	    - [request sample by period end date](sample%20messages/DWTRetrieveStatusRequest_PeriodEndDate.xml)
		- [request sample by submission key](sample%20messages/DWTRetrieveStatusRequest_SubmissionKey.xml)
        - [positive response sample](sample%20messages/DWTRetriveStatusResponse.xml)
    - RetrieveReturn
		- [request sample by period end date](sample%20messages/DWTRetrieveReturnRequest_PeriodEndDate.xml)
		- [request sample by submission key](sample%20messages/DWTRetrieveReturnRequest_SubmissionKey.xml)
        - [positive response sample](sample%20messages/DWTRetrieveReturnResponse.xml)