![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# Notifications Service 

The Notifications Service enables actionable event notifications to be retrieved by external software platforms.  

## Key Features:
* View and download [build packs for Notifications Service](Build%20Pack%20-%20Notifications.pdf)
* Notifications YAML file [Notifications.yaml](Notifications.yaml)
* Markdown view of the [Notifications.yaml](Notifications.md)

## Products using this service:

* [Employment Service](../Product%20-%20Payday%20Filing%2FEmployee%20Details)
* [Income Tax Return Service](../Product%20-%20Income%20Tax)  

## Supporting Services:

* (Required) Service: Identity and Access - view [How to integrate, OAuth requests and responses message sample and build pack](../Service%20-%20Identity%20and%20Access/Latest/) 

>**NOTE:** The included [Notifications.yaml](Notifications.yaml) file can be used along with an OpenAPI editor such as [editor.swagger.io](https://editor.swagger.io) to view technical specifications for this operation and generate example client code. 

## Sample JSON messages
---
* POST /List - Notification Service List
    * [Request body with all fields](Sample%20Files/Sample_POST_List_RequestBody.json)
    * [Request body with mandatory fields](Sample%20Files/Sample_POST_List_RequestBody_Mandatory.json)
    * [200 Response body](Sample%20Files/Sample_POST_List_ResponseBody.json)
    * [400 Response body](Sample%20Files/Sample_Error_ResponseBody.json)

## Mock Environment Information
---
### Mock Emulated Services URL
Description | URL
---|---
 Landing Page | https://mock-not.ird.digitalpartner.services
 Service Endpoint | https://mock-not.ird.digitalpartner.services/secure/gateway/notification/list 
### Mock Environment Authentication
   * Consumers of this mock service must be authenticated.
   * Authentication is provided using one of two methods:
     1. OAuth
        * OAuth token issued by the mock OAuth service. Any valid token issued by the mock OAuth service can be used to access this service.
        * Please consult the [mock OAuth service documentation](https://mock-oauth.ird.digitalpartner.services/) for further details about the authentication process.
        * The OAuth token should be provided in the 'Authorization' request header as follows:
        ```
        Authorization: Bearer {OAuthAccessToken}
        ```
     2. JWT
        * Alternatively a self-issued JWT may be used to access the service.
        * Please consult the [Notification service build pack](Build%20pack%20-%20Notifications.pdf) for information on the token structure.
        * The mock service does not validate the following JWT attributes:
            * "sub" field
            * "iss" field
            * token signature
        * The JWT should be provided in the 'Authorization' request header as follows (note the 'Bearer' prefix is omitted):
        ```
        Authorization: {JWT}
        ```
### Notification Mock Scenarios MindMap

- [View larger image](images/Notification%20Mock%20Service%20Scenarios.png)
![Mock Scenarios](images/Notification%20Mock%20Service%20Scenarios.png)

### Test data

* This table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses.
* Text in italics represents the name of the JSON node in the request.

  Scenario ID | Data | Http status | Response 
    --- | --- | --- | ---
    MOCK-NOT-001 | *FromDateTime*: "2019-10-01T14:25:31" or earlier <br> *ToDateTime*: "2019-10-01T14:25:31" or later | 200 | List with some Notifications
    MOCK-NOT-002 | *FromDateTime*: "2019-10-01T14:25:32" or earlier <br> *ToDateTime*: "2019-10-01T14:25:32" or later | 200 | List with some Notifications
    MOCK-NOT-003 | *FromDateTime*: "2019-06-01T11:16:07" or earlier <br> *ToDateTime*: "2019-06-01T11:16:07" or later | 200 | List with some Notifications
    MOCK-NOT-005 | *QueryID*: "111111111" | 200 | Empty list of Notifications
    MOCK-NOT-006 | *QueryID*: "123345185" | 200 | Empty list of Notifications
	

## URL Endpoints.
---
- Mock : https://mock-not.ird.digitalpartner.services/secure/gateway/notification/list
- Testing : https://test3.services.ird.govt.nz:4046/Gateway/notifications/list
- Pre-Production : https://test4.services.ird.govt.nz:4046/Gateway/notifications/list
- Production : https://services.ird.govt.nz:4046/Gateway/notifications/list

>**NOTE:** These endpoints are subject to change due to environment updates in the future. 