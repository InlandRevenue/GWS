![IRD logo](../Images/IRlogo.gif)
![Software Dev](../Images/SoftwareDev.png)

# Income Tax - Testing Information

## Key Documentation:

- The testing details provided on this page is applicable for all of the following invest income reporting tax types
	- [Income Tax Returns (INC)]()
	- [Donation Tax Credit](#Donation_Tax_Credit) (DTC/REB/IR5216)	

* XSD Schemas 
    * View the Income Tax XSD schema files from the [xsd](xsd/) directory
    * View and download the [return service common v2 xsd](../Service%20-%20Return/Latest/)
    * View and download the [common v2 xsd](../Schema%20-%20Common/)	
	
- Mock Environment Information
	- [Mindmap and test data](#mock-environment-information)
		
- Test Environment Information
	- [Test scenarios report template](#test-environment-information)
	- [Test Environment URLs](#test-urls)
	
- Production Environment Information
	- [Production Environment URLs](#production-environment-information)
	

---

## Mock Environment Information
---
- Mock Emulated Services URL
    - Landing page: https://mock-inc.ird.digitalpartner.services
    - Service endpoint: https://mock-inc.ird.digitalpartner.services/gateway/GWS/Returns/
- Test Scenarios
    - Income Tax Mock Scenarios Mind map
    [Mock Scenarios](images/income-tax-test-scenarios.png)
    ![Mock Scenarios](images/income-tax-test-scenarios.png) 
- Test Data
    - This table shows which scenarios (as per their numbers in the mind map) require specific data to trigger the expected responses.
    - Text in italics represents the name of the XML node in the request.
	- **For all retrieve return scenarios, the periodEndDate must be 2019-03-31.**
    
<table>
    <tbody>
        <tr>
            <th></th>
            <th>Scenario ID</th>
            <th>Operation</th>
            <th>Data</th>
        </tr>
        <tr>
            <th rowspan="5">IR3</th>
            <td>INC-ES-08</td>
            <td>RetrieveReturn</td>
            <td>Customer IRD (<em>identifier</em>): 132310297</td>
        </tr>
        <tr>
            <td>INC-ES-12</td>
            <td>RetrieveStatus</td>
            <td>Customer IRD (<em>identifier</em>): 132310297</td>
        </tr>
        <tr>
            <td>INC-ES-13</td>
            <td>RetrieveStatus</td>
            <td>Customer IRD (<em>identifier</em>): 070876272</td>
        </tr>
        <tr>
            <td>INC-ES-15</td>
            <td>Prepop</td>
            <td>Customer IRD (<em>identifier</em>): 015679840</td>
        </tr>
        <tr>
            <td colspan="2">All other scenarios</td>
            <td>Customer IRD (<em>identifier</em>): 132306907</td>
        </tr>
        <tr>
            <th>IR3NR</th>
            <td colspan="2">All scenarios</td>
            <td>Customer IRD (<em>identifier</em>): 093989910</td>
        </tr>
        <tr>
            <th rowspan="4">IR4</th>
            <td>INC-ES-24</td>
            <td>RetrieveReturn</td>
            <td>Customer IRD (<em>identifier</em>): 132329362</td>
        </tr>
        <tr>
            <td>INC-ES-28</td>
            <td>RetrieveStatus</td>
            <td>Customer IRD (<em>identifier</em>): 132329362</td>
        </tr>
        <tr>
            <td>INC-ES-29</td>
            <td>RetrieveStatus</td>
            <td>Customer IRD (<em>identifier</em>): 107031227</td>
        </tr>
        <tr>
            <td colspan="2">All other scenarios</td>
            <td>Customer IRD (<em>identifier</em>): 096062311</td>
        </tr>
        <tr>
            <th>IR4J</th>
            <td colspan="2">All scenarios</td>
            <td>Customer IRD (<em>identifier</em>): 078445386</td>
        </tr>
        <tr>
            <th>IR6</th>
            <td colspan="2">All scenarios</td>
            <td>Customer IRD (<em>identifier</em>): 079945793</td>
        </tr>
        <tr>
            <th rowspan="4">IR7</th>
            <td>INC-ES-36</td>
            <td>File</td>
            <td>Customer IRD (<em>identifier</em>): 019515842</td>
        </tr>
        <tr>
            <td>INC-ES-37</td>
            <td>File</td>
            <td>Customer IRD (<em>identifier</em>): 105493711</td>
        </tr>
        <tr>
            <td>INC-ES-38</td>
            <td>RetrieveReturn</td>
            <td>Customer IRD (<em>identifier</em>): 019515842</td>
        </tr>
        <tr>
            <td>INC-ES-39</td>
            <td>RetrieveReturn</td>
            <td>Customer IRD (<em>identifier</em>): 105493711</td>
        </tr>
        <tr>
            <th>IR8</th>
            <td colspan="2">All scenarios</td>
            <td>Customer IRD (<em>identifier</em>): 050700461</td>
        </tr>
        <tr>
            <th>IR8J</th>
            <td colspan="2">All scenarios</td>
            <td>Customer IRD (<em>identifier</em>): 113613831</td>
        </tr>
        <tr>
            <th>IR9</th>
            <td colspan="2">All scenarios</td>
            <td>Customer IRD (<em>identifier</em>): 056632778</td>
        </tr>
        <tr>
            <th>IR44</th>
            <td colspan="2">All scenarios</td>
            <td>Customer IRD (<em>identifier</em>): 052120330</td>
        </tr>
        <tr>
            <th>IR526</th>
            <td colspan="2">All scenarios</td>
            <td>Customer IRD (<em>identifier</em>): 055786372</td>
        </tr>
        <tr>
            <th>Authorisation</th>
            <td>INC-ES-01</td>
            <td>All</td>
            <td>Customer IRD (<em>identifier</em>): 111001111</td>
        </tr>
        <tr>
            <th rowspan="5">Error Scenarios</th>
            <td>INC-ES-52</td>
            <td>File</td>
            <td>Return with multiple IR10 attachments</td>
        </tr>
        <tr>
            <td>INC-ES-53</td>
            <td>RetrieveReturn</td>
            <td>Customer IRD (<em>identifier</em>): 107031227</td>
        </tr>
        <tr>
            <td>INC-ES-54</td>
            <td>File</td>
            <td>IR9 return with IR307 attachment</td>
        </tr>
        <tr>
            <td>INC-ES-55</td>
            <td>File</td>
            <td>IR3 return with:<br>
                <em>totalPAYEDeducted</em> &gt; <em>totalGrossIncome</em><br>
                <em>totalIncomeNotLiableForACCLevy</em> &gt; <em>totalGrossIncome</em><br>
                <em>totalExtinguishedTCPDs</em> &gt; <em>totalTCPDs</em>
            </td>
        </tr>
        <tr>
            <td>INC-ES-56</td>
            <td>RetrieveFilingObligations</td>
            <td>Customer IRD (<em>identifier</em>): 078650362</td>
        </tr>
    </tbody>
</table>

## Mock Environment:
-----------------

- Mock URLs:
	- Mock Emulated Services	-	https://mock-inc.ird.digitalpartner.services/ 
	- Mock URL Endpoint			- 	https://mock-inc.ird.digitalpartner.services/gateway/GWS/Returns/

- Returns Service Mappings - (default) port 443 of path "/gateway/GWS/Returns":
	- /gateway/GWS/Returns?wsdl - WSDL is not available, returning HTTP 200 only.
	
- WS-addressing ```action``` header value of the incoming request is mapped to an endpoint:
	- FileReturns 		-	https://services.ird.govt.nz/GWS/Returns/Return/File
	- RetrieveReturns 	-	https://services.ird.govt.nz/GWS/Returns/Return/RetrieveReturn
	- RetrieveStatus 	-	https://services.ird.govt.nz/GWS/Returns/Return/RetrieveStatus
	- Prepop   	-	https://services.ird.govt.nz/GWS/Returns/Return/Prepop
	- RetrieveFilingObligations   	-	https://services.ird.govt.nz/GWS/Returns/Return/RetrieveFilingObligations
	 
- Authentication: 
	- Authentication is based on the outcome of OAuth token validation (using new [OAuth emulator](https://mock-oauth.ird.digitalpartner.services/))
	- Incoming requests should include "Authorization" header with the OAuth token value
	- In case of missing token, emulated service would respond with error statusCode 2

- Schema Validations:
	- In case of failure XML validation failure response (error code 21)

- Then the service operation specific validations are carried out and returned with appropriate response (per mind map).
- Unmatched requests will return an appropriate HTTP response status

## Test Environment Information:
-----------------

* Test Environment URL Endpoints

	* Cloud Gateway Service: `https://test3.services.ird.govt.nz:4046/gateway/gws/returns/`
	* Native Desktop Gateway Service: `https://test3.services.ird.govt.nz/gateway2/gws/returns/`
	* Cloud SOAP WSDL: `https://test3.services.ird.govt.nz:4046/gateway/gws/returns/?wsdl`
	* Native Desktop SOAP WSDL: `https://test3.services.ird.govt.nz/gateway2/gws/returns/?wsdl`
            
## Production Environment Information:
-----------------

* Production URL Endpoints

	- Cloud Gateway Service: `https://services.ird.govt.nz:4046/gateway/gws/returns/`
	- Native Desktop Gateway Service: `https://services.ird.govt.nz/gateway2/gws/returns/`
	- (Cloud) SOAP WSDL: `https://services.ird.govt.nz:4046/gateway/gws/returns/?wsdl`
	- (Native Desktop) SOAP WSDL: `https://services.ird.govt.nz/gateway2/gws/returns/?wsdl`	
   	