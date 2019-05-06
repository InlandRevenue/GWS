![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

Approved issuer levy (AIL) Software Development Kit (SDK) for Investment Income Reporting
=======================================

Key Documentation:
-------------

- Business use cases
	- [Download and view](III%20-%20AIL%20-%20GWS%20business%20use%20cases.pdf)
	
- Schemas and WSDLS
	- View and download the [common v2 xsd](../../Schema%20-%20Common/Common.v2.xsd)
	- View and download the [return service common v2 xsd](../../Service%20-%20Return/Latest/ReturnCommon.v2.xsd)
	- View and download the AIL return [XSD](ReturnAIL.v0.xsd) and [WSDL](AILDevWsdl.wsdl) from this current directory
	
- Return Service - Investment Income Reporting
	- [Download the build pack](../Service%20-%20Return%20III/Latest/Gateway%20Services%20Build%20Pack%20-%20Return%20Service%20-%20III.pdf) to view data definitions of each operation and response status code definitions
	
- Message Samples
    - [View Message samples for requests and positive responses](#message-samples)

- Mock Environment Information
	- [Mindmap and test data](../Test%20Details%20-%20IIR/README.md#mock-environment-information)
	- [Requests Matching Logic](../Test%20Details%20-%20IIR/README.md#mock-environment-requests-matching-logic)

- Test Environment Information
	- [Test scenarios report template and mindmap](../Test%20Details%20-%20IIR/README.md#test-environment-information)

- Identity and Access Services
	- [How to Integrate with OAuth](../../Service%20-%20Identity%20and%20Access/Latest/OAuth%20Authentication%20-%20How%20to%20Integrate.md)
	- [Message Samples](../../Service%20-%20Identity%20and%20Access/Latest/) - OAuth requests and responses
	- [Download the build pack](../../Service%20-%20Identity%20and%20Access/Latest/Build%20pack%20-%20Identity%20and%20Access%20Services.pdf) - for OAuth 2.0 implementation   

- Investment Income Reporting:
	- [Testing Information](../Test%20Details%20-%20IIR/README.md)
	- [Mock URL Endpoints](../Test%20Details%20-%20IIR/README.md#mock-environment)
	- [Test URL Endpoints](../Test%20Details%20-%20IIR/README.md#test-environment-information)
	- [Production URL Endpoints](../Test%20Details%20-%20IIR/README.md#production-environment-information)	

Message samples:
-----------------

- Simulating AIL Returns Operations:
    - File
		- [request sample](sample%20messages/AILFileRequest.xml)
        - [positive response sample](sample%20messages/AILFileResponse.xml)
	- File Amendment
		- [request sample as single filer](sample%20messages/AILFileRequestUpdate_SingleFiler.xml)
		- [request sample as multi filer](sample%20messages/AILFileRequestUpdate_MultiFiler.xml)
        - [positive response sample](sample%20messages/AILFileResponse.xml)
    - RetrieveStatus
	    - [request sample by period end date](sample%20messages/AILRetrieveStatusRequest_PeriodEndDate.xml)
		- [request sample by submission key](sample%20messages/AILRetrieveStatusRequest_SubmissionKey.xml)
        - [positive response sample](sample%20messages/AILRetriveStatusResponse.xml)
    - RetrieveReturn
		- [request sample as single filer](sample%20messages/AILRetrieveReturnRequest_SingleFiler.xml)
		- [request sample as multi filer](sample%20messages/AILRetrieveReturnRequest_MultiFiler.xml)
        - [positive response sample](sample%20messages/AILRetrieveReturnResponse.xml)


