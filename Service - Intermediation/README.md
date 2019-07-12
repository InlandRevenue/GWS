![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# Intermediation Service

Intermediation is the process of linking a business intermediary (such as a tax agent, 
bookkeeper, payroll bureau, payroll intermediary etc) to an individual or organisation 
so the intermediary can act on their behalf for tax purposes. 

The Intermediation Gateway Service provides the ability for intermediaries to:
- manage links to clients (link, delink and update) 
- retrieve clients and client lists that are already established.

## Key Documentation:

- Schemas and WSDLs:
	- View and download the [Common v2 xsd](../Schema%20-%20Common/Common.v2.xsd)
	- View and download the Intermediation [XSD](Latest/Intermediation.v1.xsd) and [WSDL](Latest/IntermediationDevWsdl.v1.wsdl)
	
- Intermediation Service 
	- [Download the build pack](Latest/Gateway%20Services%20Build%20Pack%20-%20Intermediation%20Service.pdf) to view data definitions of each operation and response status code definitions
	
* Message Samples
	* [View message samples for requests and positive responses](#Messages-Samples)


## Environment Information: 	
	
- [Mock Environment Information](#Mock-Environment-Information)
- [Test Environment Information](#Test-Environment-Information)
- [Production Environment Information](#Production-Environment-Information)

## Supporting Services:

* Service: Identity and Access - view [How to integrate, OAuth requests and responses message sample and build pack](../Service%20-%20Identity%20and%20Access/Latest/) 

---

## Mock Environment Information:
-----------------

* Mock Emulated Services URL
	* https://mock-int.ird.digitalpartner.services/ 

* Test Scenarios 	
	- Intermediation Information Test Scenarios Mindmap
	![Test Scenarios](images/Intermediation-test-scenarios.png)	

* Test Data
	* The following test data can be tested in our Mock Services environment when submitting requests to the service operations
	* This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses. 

> The following intermediary, client lists and linked clients are provided by the emulated service:

| *Intermediary id* | *Client list type* | *List id* | *List id type* | *Refund Account* | *Client Id* | *Linked* |
| --- | --- | --- | --- | --- | --- | --- | --- | 
|132261132|Tax Agent|132261132|LSTID|No|132260737|AIL,AIP,EMP,FAM,FBT,GSD,GST,INC,IPS,NRT,REB,RLT,RWT,SLS|
| |Tax Agent|132261555|LSTID|Yes|132260818|AIL,AIP,DWT,EMP,FBT,GMD,GSD,GST,INC,IPS,MPO,NRT,PIE,RLT,RWT|
| | | | | | 132260806|REB|
| | Tax Agent|132261571|LSTID|Yes|132260753|master,GST,INC|
| | | | | | 132260774|EMP|
| | | | | | 132260806|FBT|
| | Tax Agent|132261660|LSTID|No|083230304|GST|
| | | | | | 132293525| CRS,FAT |
| | | | | |085078534 | PRS | 077415807 | EMP |
| | PAYE Intermediary | 132280722 | LSTID | No | 077415807 | EMP |
| | | | | | 132260753 | EMP |
| | | | | | 132260806 | EMP |
| | Bookkeeper | 1039039 | CLTLID | No | 077415807 | EMP |
| | | | | | 132260806 | INC | 
| | Other Representative | 1089042 | CLTLID | No | 077415807 | EMP |
| | | | | | 132260806 | NRT | 
| | Payroll Bureau | 1039040 | CLTLID | No | 077415807 | EMP |
| | | | | | 132260806| EMP |	

> The following clients are defined by the emulated service but are not linked:

| *Client id* | *Client account types* |
| --- | --- | 
| 132260753| AIL,AIP,FBT,GSD,IPS,NRT,REB,RLT,RWT |
| 132260958 | AIL,AIP,DWT,EMP,FBT,GMD,GSD,INC,IPS,MPO,NRT,PIE,RLT,RWT |
| 132269289 | AIL,AIP,EMP,FAM,FBT,GSD,GST,INC,IPS,NRT,REB,RWT,SLS |

## Messages Samples

* RetrieveClient
	* [RetrieveClient Request](sample%20messages/RetrieveClient-request.xml)
	* [RetrieveClient Response](sample%20messages/RetrieveClient-response.xml)

* RetrieveClientList
	* [RetrieveClientList Request](sample%20messages/RetriveClientList-request.xml)
	* [RetrieveClientList Response](sample%20messages/RetriveClientList-response.xml)

* Link
	* [Link Request](sample%20messages/Link-request.xml)
	* [Link Response](sample%20messages/Link-response.xml)

* Delink
	* [Delink Request](sample%20messages/Delink-request.xml)
	* [Delink Response](sample%20messages/Delink-response.xml)

* Update
	* [Update Request](sample%20messages/Update-request.xml)
	* [Update Response](sample%20messages/Update-response.xml)




## Test Environment Information:
-----------------

* Test Scenarios
	- [Download test scenarios report template](Intermediation%20Service%20-%20Test%20Scenarios%20Report%20Template.docx)

* Test Environment URL Endpoints
	
	* Cloud Gateway Service: https://test3.services.ird.govt.nz:4046/gateway/gws/intermediation/
	* Native Desktop Gateway Service: https://test3.services.ird.govt.nz/gateway2/gws/intermediation/
	* Cloud SOAP WSDL: https://test3.services.ird.govt.nz:4046/gateway/gws/intermediation/?wsdl
	* Native Desktop SOAP WSDL: https://test3.services.ird.govt.nz/gateway2/gws/intermediation/?wsdl
            
## Production Environment Information:
-----------------

* Production URL Endpoints

	- Cloud Gateway Service: https://services.ird.govt.nz:4046/gateway/gws/intermediation/
	- Native Desktop Gateway Service: https://services.ird.govt.nz/gateway2/gws/intermediation/
	- (Cloud) SOAP WSDL: https://services.ird.govt.nz:4046/gateway/gws/intermediation/?wsdl
	- (Native Desktop) SOAP WSDL: https://services.ird.govt.nz/gateway2/gws/intermediation/?wsdl
	
