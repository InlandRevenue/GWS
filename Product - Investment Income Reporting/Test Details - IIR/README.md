![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# Investment Income Reporting - Testing Information

- The testing details provided on this page is applicable for all of the following invest income reporting tax types
	- Approved Issuer Levey (AIL)
	- Dividend Withholding Tax (DWT)
	- Interest Pay as you go (IPS)
	- Non Resident Withholding Tax (NRT) 
	- Resident Withholding Tax (RWT)

- Mock Environment Information
	- [Mindmap and test data](#mock-environment-information)
	- [Requests Matching Logic](#mock-environment-requests-matching-logic)
	
- Test Environment Information
	- [Test scenarios report template](#test-environment-information)
	- [Test Environment URLs](#test-urls)
	
- Production Environment Information
	- [Production Environment URLs](#production-environment-information)
	
	
Mock Environment Information:
-----------------

- Investment Income Reporting Mock Scenarios Mindmap
	
	- [View larger image](images/IIR-mockServiceScope-scenarios.png)
	![Mock Scenarios](images/IIR-mockServiceScope-scenarios.png)

- Test Data
	- The following test data can be tested in our Mock Services environment when submitting requests to the service operations for the following invest income reporting tax types (AIL / DWT/ IPS/ NT / RWT)
	
		- Valid Identifiers per tax type:
			- AIL: 	[123768566, 132145202]
			- DWT:	[123769066, 132145202]
			- IPS: 	[123752058, 132145202]
			- NRT: 	[123768973, 132145202]
			- RWT: [123768736, 132145202]

		- Valid Submission Keys:
			- these can be used across all IIR tax types and operations:
			- [294502400, 1333370880, 463962112, 1859829760, 1699905536, 1154154496, 1783480320]
			
		- Valid Primary IRD numbers: [123671791, 123769651] 
		
	- This following table shows which scenarios (as per their numbers in the mindmap) require specific data to trigger the expected responses.
	- Text in italics represents the name of the XML node in the request.
	
	

| Test ID | Test Module  | Example Data | Remarks |
| --- | --- | --- | --- |
| <span style="white-space: nowrap;">IIR-ES-001</span> |  Authentication            | -                      |  Set no authentication token |
| IIR-ES-002 |  Authentication            | -                      |  Set invalid authentication |token |
| IIR-ES-004 |  File Operation            | `132145202`               |  Set valid IRD number / |identifier value |
| IIR-ES-005 |  File Operation            | `11`                      |  Set reference Id, amendType 'U' |
| IIR-ES-006 |  File Operation            | `5312572871`              |  Set lineNumber, amendType 'D' |
| IIR-ES-007 |  File Operation            | `132145202`               |  AmendType 'A' |
| IIR-ES-008 |  Retrieve Return Operation | `294502400`               |  Include submissionKey |
| IIR-ES-009 |  Retrieve Status Operation | `1333370880`              |  Include submissionKey |
| IIR-ES-010 |  Retrieve Status Operation | -                     |  Do not set submission key |in request |
| IIR-ES-011 |  Error Handling            | minorFormType: `''`         |  Set empty value for |minorFormType |
| IIR-ES-012 |  Error Handling            | Identifier: `123456789` |  Set Identifier value |
| IIR-ES-013 |  Error Handling            | -                     |  Include  |creditTransferRequest element in request payload |
| IIR-ES-014 |  Error Handling            | -                     |  No submission key in retrieve request payload |
| IIR-ES-015 |  Error Handling            | -                     |  No submission key in amend request payload |
| IIR-ES-016 |  Error Handling            | minorFormType: `''` majorFormType: `''`|  Set empty value for majorFormType and minorFormType |
| IIR-ES-017 |  Error Handling            | TaxType: `NRT`incomeType: `NRDIV` |  No dividend fields in request  |
| IIR-ES-018 |  Error Handling            | TaxType: `NRT`incomeType: `NRINT` |  any valid NRT income type other than NRDIV<br/>but with dividend fields |
| IIR-ES-019 |  Error Handling            | - |  NRT (incomeType: NRDIV) / DWT request <br/>with missing number share field |
| IIR-ES-020 |  Error Handling            | - |  NRT (incomeType: NRDIV) / DWT request <br/>with missing dividend declared date field |
| IIR-ES-021 |  Error Handling            | - |  NRT (incomeType: NRDIV) / DWT request <br/>with  missing payment date field | 



			
Mock Environment:
-----------------

- Mock URLs:
	- Mock Emulated Services	-	https://mock-iir.ird.digitalpartner.services/ 
	- Mock URL Endpoint			- 	https://mock-iir.ird.digitalpartner.services/gateway/GWS/Returns/

- Returns Service Mappings - (default) port 443 of path "/gateway/GWS/Returns":
	- /gateway/GWS/Returns?wsdl - WSDL is not available, returning HTTP 200 only.
	
- WS-addressing ```action``` header value of the incoming request is mapped to an endpoint:
	- FileReturns 		-	https://services.ird.govt.nz/GWS/Returns/Return/File
	- RetrieveReturns 	-	https://services.ird.govt.nz/GWS/Returns/Return/RetrieveReturn
	- RetrieveStatus 	-	https://services.ird.govt.nz/GWS/Returns/Return/RetrieveStatus
	 
- Authentication: 
	- Authentication is based on the outcome of OAuth token validation (using new OAuth emulator)
	- Incoming requests should include "Authorization" header with the OAuth token value
	- In case of missing token, emulated service would respond with error statusCode 2

- Schema Validations:
	- In case of failure XML validation failure response (error code 21)

- Account type value is then verified to asses it is valid III product request.
	- if not, an invalid account type error is returned.

- Then the service operation specific validations are carried out and returned with appropriate response (per mind map).
- Unmatched requests will return an appropriate HTTP response status

Test Environment Information:	
-----------------  

- Test Scenarios
	- [Download AIL test scenarios report template](Investment%20Income%20Reporting%20-%20Tax%20Type%20-%20AIL%20-%20%20Test%20Scenarios%20Report%20Template.docx)
	- [Download DWT test scenarios report template](Investment%20Income%20Reporting%20-%20Tax%20Type%20-%20DWT%20-%20%20Test%20Scenarios%20Report%20Template.docx)
	- [Download IPS test scenarios report template](Investment%20Income%20Reporting%20-%20Tax%20Type%20-%20IPS%20-%20%20Test%20Scenarios%20Report%20Template.docx)
	- [Download NRT test scenarios report template](Investment%20Income%20Reporting%20-%20Tax%20Type%20-%20NRT%20-%20%20Test%20Scenarios%20Report%20Template.docx)
	- [Download RWT test scenarios report template](Investment%20Income%20Reporting%20-%20Tax%20Type%20-%20RWT%20-%20%20Test%20Scenarios%20Report%20Template.docx)

- Test URL Endpoint:
    - Cloud Gateway Service: https://test3.services.ird.govt.nz:4046/gateway/gws/returns/
    - Native Desktop Gateway Service: https://test3.services.ird.govt.nz/gateway2/gws/returns/
	
- Test WSDL URL Endpoint:
	- Cloud Gateway Service: https://test3.services.ird.govt.nz:4046/gateway/gws/returns/?wsdl
    - Native Desktop Gateway Service: https://test3.services.ird.govt.nz/gateway2/gws/returns/?wsdl
	


Production Environment Information:
-----------------  

- Production URL Endpoint:
    - Cloud Gateway Service: https://services.ird.govt.nz:4046/gateway/gws/returns/
    - Native Desktop Gateway Service: https://services.ird.govt.nz/gateway2/gws/returns/
	
- Production WSDL URL Endpoint:
	- Cloud Gateway Service: https://services.ird.govt.nz:4046/gateway/gws/returns/?wsdl
    - Native Desktop Gateway Service: https://services.ird.govt.nz/gateway2/gws/returns/?wsdl	