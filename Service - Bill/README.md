![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# Return Status Push Notifications Service 

This service is an application programming interface (API) that external applications can call in real-time to retrieve information for a particular customer bill item. The response also includes provisional tax method details and history associated to the account to which the bill item belongs. 
 
The objective of this API is to allow transaction data services (TDS) software providers to query information that was formerly available in the Tax Agent Web Services (TAWS) data feed. 


## Key Documentation
---
- YAML file:
	- View and download the [Customer API YAML](Customer%20API.yaml)

- Income API Build Pack 
	- [Download the build pack](Build%20pack%20-%20Bill%20API.pdf) to view data definitions of each operation and response status code definitions
	
## Supporting services
---
- Service: Identity and Access - view: [How to integrate, OAuth requests and responses message samples and build pack](../Service%20-%20Identity%20and%20Access/Latest/)	
	
- Message Samples
	* [View message samples for requests and responses](#-message-samples)

## Message Samples
---
* Sample JSON payload messages:
	* Request
		* [Request](sample%20messages/request.json)
			
	* Positive response
	    * [Positive response](sample%20messages/response_positive_response.json)			
	
## Products using this service:
* [Transaction Data Services TDS](../Product%20-%20Transaction%20Data%20Services/)

### Test environment URL
| End point|  URL|
|--|--|
| Testing | https://test3.services.ird.govt.nz:4046/gateway/document/{operation}|    
| Pre-Production | https://test4.services.ird.govt.nz:4046/gateway/document/{operation} | 

>**NOTE:** These endpoints are subject to change due to environment updates in the future. 

### Prod environment URL
| End point|  URL|
|--|--|
| Production | https://services.ird.govt.nz:4046/gateway/document/{operation} |
