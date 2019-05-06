![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

Non-resident withholding tax (NRT) Software Development Kit (SDK) for Investment Income Reporting
=======================================

Key Features:
-------------

- Business use cases
	- [Download and view](III%20-%20NRT%20-%20GWS%20business%20use%20cases.pdf)
	
- Schemas and WSDLs
	- View and download the [common v2 xsd](../Schema%20-%20Common%20III/)
	- View and download the [Return Service common v2 xsd](../Service%20-%20Return%20III/Latest/)
	- View and download the NRT return [XSD](ReturnNRT.v0.xsd) and [WSDL](NRTDevWsdl.wsdl) from this current directory
	
- Returns Service - Investment Income Information 
	- [Download the build pack](../Service%20-%20Return%20III/Latest/Gateway%20Services%20Build%20Pack%20-%20Return%20Service%20-%20III.pdf) to view data definitions of each operation and response status code definitions
	
- Identity and Access Services
	- [How to Integrate with OAuth](../../Service%20-%20Identity%20and%20Access/Latest/OAuth%20Authentication%20-%20How%20to%20Integrate.md)
	- [Message Samples](../../Service%20-%20Identity%20and%20Access/Latest/) - OAuth requests and responses
	- [Download the build pack](../../Service%20-%20Identity%20and%20Access/Latest/Build%20pack%20-%20Identity%20and%20Access%20Services.pdf) - for OAuth 2.0 implementation   

- Mock URL Endpoint:            
    - https://mock-iir.ird.digitalpartner.services/gateway/GWS/Returns/

- Test URL Endpoint:
    - Cloud Gateway Service: https://test3.services.ird.govt.nz:4046/gateway/gws/returns/
    - Native Desktop Gateway Service: https://test3.services.ird.govt.nz/gateway2/gws/returns/
            
- Production URL Endpoint:
    - Cloud Gateway Service: https://services.ird.govt.nz:4046/gateway/gws/returns/
    - Native Desktop Gateway Service: https://services.ird.govt.nz/gateway2/gws/returns/