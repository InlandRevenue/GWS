![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Interest pay as you earn (IPS) Software Development Kit (SDK) for Investment Income Reporting

## Key Documentation:

- Business use cases
	- [Download and view](III%20-%20IPS%20-%20GWS%20business%20use%20cases.pdf)
	
- Schemas and WSDLs
	- View and download the [common v2 xsd](../../Schema%20-%20Common/Common.v2.xsd)
	- View and download the [return service common v2 xsd](../../Service%20-%20Return/Latest/ReturnCommon.v2.xsd)
	- View and download the IPS return [XSD](ReturnIPS.v1.xsd) and [WSDL](IPSDevWsdl.wsdl) from this current directory
	
- Returns Service - Investment Income Information 
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

## Supporting Services: 

- Service: Identity and Access – view[ How to integrate, OAuth requests and responses message sample and build pack](../../Service%20-%20Identity%20and%20Access/Latest/)   

## Message Samples:
-----------------

- File
    - [request sample](sample%20messages/IPSFileRequest.xml)
    - [positive response sample](sample%20messages/IPSFileResponse.xml)
- File Amendment
    - [request sample as single filer](sample%20messages/IPSFileRequestUpdate_SingleFiler.xml)
    - [request sample as multi filer](sample%20messages/IPSFileRequestUpdate_MultiFiler.xml)
    - [positive response sample](sample%20messages/IPSFileResponse.xml)
- RetrieveStatus
    - [request sample by period end date](sample%20messages/IPSRetrieveStatusRequest_PeriodEndDate.xml)
    - [request sample by submission key](sample%20messages/IPSRetrieveStatusRequest_SubmissionKey.xml)
    - [positive response sample](sample%20messages/IPSRetriveStatusResponse.xml)
- RetrieveReturn
    - [request sample as single filer](sample%20messages/IPSRetrieveReturnRequest_SingleFiler.xml)
    - [request sample as multi filer](sample%20messages/IPSRetrieveReturnRequest_MultiFiler.xml)
    - [positive response sample](sample%20messages/IPSRetrieveReturnResponse.xml)
            
