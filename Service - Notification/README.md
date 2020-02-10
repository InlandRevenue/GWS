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

## URL Endpoints.
---
- Mock : https://mock-not.ird.digitalpartner.services/secure/gateway/GWS/Notification/list
- Testing : https://test3.services.ird.govt.nz:4046/Gateway/notifications/list
- Pre-Production : https://test4.services.ird.govt.nz:4046/Gateway/notifications/list
- Production : https://services.ird.govt.nz:4046/Gateway/notifications/list

>**NOTE:** These endpoints are subject to change due to environment updates in the future. 