![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# Bill API

This service is an application programming interface (API) that external applications 
can call in real-time to retrieve information for a particular customer bill item. The 
response also includes provisional tax method details and history associated to the 
account to which the bill item belongs. 
 
The objective of this API is to allow transaction data services (TDS) software providers 
to query information that was formerly available in the Tax Agent Web Services 
(TAWS) data feed. 

## Key Documentation
---
- YAML file:
	- View and download the [Bill API YAML](Bill%20API%202020-03-09.yaml)

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

## Mock Environment Information
---
### Mock Emulated Services URL
Description | URL
---|---
 Landing Page | https://mock-bil.ird.digitalpartner.services
 Service Path | https://mock-bil.ird.digitalpartner.services/secure/gateway/bill/bill/
### Mock Environment Authentication
   * Consumers of this mock service must be authenticated.
   * Access delegation/restriction is not emulated, and any authenticated user has access to the test data.
   * Authentication is provided by an OAuth token issued by the mock OAuth service. Any valid token issued by the mock OAuth service can be used to access this service. Please consult the [mock OAuth service documentation](https://mock-oauth.ird.digitalpartner.services/) for further details about the authentication process.
   * The OAuth token should be provided in the 'Authorization' request header as follows:
   ```
   Authorization: Bearer {OAuthAccessToken}
   ```
### Document Mock Scenarios MindMap

- [View larger image](images/BillAPI%20Mock%20Service%20Mindmap.png)
![Mock Scenarios](images/BillAPI%20Mock%20Service%20Mindmap.png)

### Test data

* This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses.
* Text in italics represents the name of a request header or field in the request body.

  Scenario ID | Data | Http status | Response 
    --- | --- | --- | ---
    MOCK-BILL-001 | *Bill.Id*: "1058166784" | 200 | Bill Item & Provisional Tax details
    MOCK-BILL-002 | *Bill.Id*: "1411815424" | 200 | Bill Item & Provisional Tax details
    MOCK-BILL-003 | *Bill.Id*: "865310720" | 200 | Bill Item & Provisional Tax details
    MOCK-BILL-004 | *Bill.Id*: "282290176" | 200 | Bill Item & Provisional Tax details
    MOCK-BILL-005 | *Bill.Id*: "1804888576" | 401 | EV1022 - Unauthorised delegation.
    MOCK-BILL-008 | *Bill*: {"Invalid": true} | 400 | EV1100 - Incoming content contains invalid field names or field/value lengths exceeding 255 characters.
    MOCK-BILL-009 | *Bill*: {} | 400 | EV2000 - Mandatory field - Bill.Id  - is missing
    MOCK-BILL-010 | *Bill.Id*: "123" | 404 | ER5000 - No bill item found with input data
    MOCK-BILL-011 | *Authorization*: "Bearer invalidtoken" | 401 | EV1020 - Authentication error
    MOCK-BILL-012 | *Authorization*: (empty) | 401 | EV1021 - Missing OAuth in the HTTP header


### Test environment URL
| End point|  URL|
|--|--|
| Mock | https://mock-bil.ird.digitalpartner.services/secure/gateway/bill/ |
| Testing | https://test3.services.ird.govt.nz:4046/gateway/bill/|    
| Pre-Production | https://test4.services.ird.govt.nz:4046/gateway/bill/ | 

>**NOTE:** These endpoints are subject to change due to environment updates in the future. 

### Prod environment URL
| End point|  URL|
|--|--|
| Production | https://services.ird.govt.nz:4046/gateway/bill/ |
