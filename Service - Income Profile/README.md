![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# Income Profile API
---

The Income Profile API described in this build pack document provides a mechanism for external partners to retrieve income data reported to Inland Revenue.

>**NOTE:** The Income Profile Service is only available to Digital Service Providers who use X.509 Digital Certificate used for Mutual TLS on port 4046 and requires OAuth2 token.
 


## Key Documentation
---

- YAML file:
	- View and download the [IncomeProfile.yaml](IncomeProfile.yaml)

- Income Profile Build Pack 
	- [Download the build pack](Gateway%20Services%20Build%20pack%20-%20Income%20Profile%20API.pdf) to view data definitions of each operation and response status code definitions
	
* Message Samples
	* [View message samples for requests and responses](#-message-samples)

* Mindmap
    * [View Mock scenarios Mindmap](#-mock-scenarios-mindmap)

>**NOTE:** The emulated service is not managing authentication. Access delegation/restriction is not emulated and any user has access to the test data.
        
* Test data
    * [View test data for Mock service](#-test-data-for-mock-service)

* URL endpoints
    * [View URL endpoints](#-url-endpoints)
    
* Supporting services
    * Service: Identity and Access - view: [How to integrate, OAuth requests and responses message samples and build pack](../Service%20-%20Identity%20and%20Access/Latest/)
    
## Mock scenarios Mindmap
---

- [View larger image](images/Income%20API%20Emulator%20Mindmap.png)
![Mock Scenarios](images/Income%20API%20Emulator%20Mindmap.png)


## Message Samples
---

* Sample JSON payload messages
	* Requests
	    * [Request with end date](sample%20messages/request_with_end_date.json)
	    * [Request without end date](sample%20messages/request_without_end_date.json)
	    
	* Positive response
	    * [Positive response](sample%20messages/response_positive_response.json)
	  
	* Negative response - http 400
	    * [EV1022 - Access is not permitted](sample%20messages/response_EV1022_access_is_not_permitted.json)
	    * [EV1100 - Invalid input parameter](sample%20messages/response_EV1100_invalid_input_parameter.json)
	    * [EV1200 - Exceeds the maximum limit](sample%20messages/response_EV1200_exceed_the_max_limit.json)
	    * [EV2234 - IR number failed check digitd](sample%20messages/response_EV2234_IR_failed_check_digit.json)
	    * [EV2235 - IR number not found](sample%20messages/response_EV2234_IR_failed_check_digit.json)
	    
	* Negative response - http 416
	    * Emulator body: "Requested Range Not Satisfiable"
	    * Production or test environment: body is empty. Http status reasonPhrase: "Requested Range Not Satisfiable"


## Test data for Mock Service
---
   - The following test data can be tested in our Mock Services environment when submitting requests to the service operations
   - This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses.

      Scenario ID | Data: IRD number | Http status | Response 
    	--- | --- | --- | ---
    	MOCK-01, MOCK-02 | 019542033, 027083307, 069164331, 059637355, 081526583. Date range must include at least one day between 2013-07-31 and 2069-11-04 | 200 | List of Income Profile
    	MOCK-10 | 123612507 | 400 | EV1022 - Access is not permitted for the requester to perform this operation for the submitted identifier
    	MOCK-11, MOCK-12, MOCK-13, MOCK-14, MOCK-15, MOCK-16, MOCK-17 | Any IRD number. E.g. 019542033. Request must be updated according to the scenario | 400 | EV1100 - Invalid input parameters. Please check documentation
    	MOCK-20 | 123346718 | 400 | EV1200 - The number of records retrieved exceeds the maximum limit
    	MOCK-30 | 111888222 | 400 | EV2234 - IR number failed check digit
    	MOCK-40 | 123350375 | 400 | EV2235 - IR number not found
    	MOCK-50 | 019542033, 027083307, 069164331, 059637355, 081526583. Date range must exclude days between 2013-07-31 and 2069-11-04 | 416 | Empty response body
    	MOCK-51 | Any IRD number not used in any other scenarios. E.g. 023123023 | 416 | Empty response body


## URL Endpoints
---

| End point|  URL|
|--|--|
| Mock | https://mock-ipr.ird.digitalpartner.services/secure/gateway/income/profile/list |
| Testing | https://test3.services.ird.govt.nz:4046/gateway/income/profile/list |    
| Pre-Production | https://test4.services.ird.govt.nz:4046/gateway/income/profile/list | 
| Production | https://services.ird.govt.nz:4046/gateway/income/profile/list |

>**NOTE:** These endpoints are subject to change due to environment updates in the future. 