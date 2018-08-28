![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

OAuth Authentication - How to Integrate
=======================================

Key Features:
-------------

- [Simulating Authentication Flow](#simulating-authentication-flow)

- [Full authentication steps](#full-authentication-steps)
    - Issuing OAuth Access Token
    - Validating OAuth Access Token

- [Sample Curl commands](#sample-curl-commands)
	- Request OAuth Code
	- Get OAuth Code
	- Get OAuth Token 
	- API call to Smoke Test (Prepop Operation)

Simulating Authentication Flow:
-----------------
	
High Level Flow
![High Level Flow](images/high_level_flow.jpg)
	
Sequence Diagram
![Sequence Diagram](images/sequence_diagram.png)

Full authentication steps:
----------------- 
	- In our gateway services environments OAuth service is used, so as a service provider you would need to trigger customer's behaviour to complete this OAuth flow.
        1. Customer accesses the Client Application via browser. They take an action that requires access to IR Gateway Services.
        2. The Client Application invokes the OAuth Server to get access token, the customer's browser is redirected to IR login page.
            At this step as a service provider you need to send a HTTP GET request to OAuth Server, url format as below:
            > https://{EmulatedServiceHost}:{AuthServicePort}/ms_oauth/oauth2/endpoints/oauthservice/authorize?client_id={ClientID}&redirect_uri={RedirectURI}&scope={Scope}&response_type=code
       
            - Parameters:
                - {ClientID}: a valid Client identifier, see Valid Clients table below
                - {RedirectURI}: Client Application's redirect URI
                - {Scope}: e.g. MYIR.Services
				
				- Valid Clients - in Mock Services Environment
				Client Id | Client Secret | Has users
				--- | --- | ---
				TestClient1 | TestClient1Secret | yes
				TestClient2 | TestClient2Secret | no
				
        3. Customer login to MyIR and consent - Customer submits credentials, consent page and redirection pages are skipped in this emulated service.
            At this step as a service provider you need to send a HTTP POST request to OAuth Server.
            Url format:
			> https://{ServiceHostdomain}/oam/server/auth_cred_submit
			
			- Parameters:
                - {ServiceHostdomain}: this is IR's gateway service environment specific domain that is accessed after your endpoint IP / CIDR range is white-listed. 
            
            - Request headers MUST include:
            > Content-Type: application/x-www-form-urlencoded
            > Cookie: {CookieFromLastStep}
            
            - Request body: 
            > userid={CustomerUserID}&password={CustomerUserPassword}&login=Login

            - Parameters:
                - {CustomerUserID}: **can be anything for clients that have users (see Valid Clients table above).**
                - {CustomerUserPassword}: **can be anything for clients that have users (see Valid Clients table above).**	
        4. Authorization Code returns to Client Application by a HTTP 302 redirection to the redirectURI.
            - Response url format:
            > https://{RedirectURI}?code={AuthorizationCode}

            - Parameters:
                    - {RedirectURI}: Client Application's redirect URI
                    - {AuthorizationCode}: the Authorization Code to be used for retrieving an access token	
        5. Client Application retrieves OAuth Access Token by sending Authorization Code as well as Client Application's credentials
            Url format:
            > https://{ServiceHostdomain}/ms_oauth/oauth2/endpoints/oauthservice/tokens
			
			- Parameters:
                - {ServiceHostdomain}: this is IR's gateway service environment specific domain that is accessed after your endpoint IP / CIDR range is white-listed.

            - Request headers MUST include:
            > Authorization: Basic {ClientApplicationEncodedCredentials}
            > Content-Type: application/x-www-form-urlencoded 

            - Parameters:
                - {ClientApplicationEncodedCredentials}: the encoded Client Application's credentials, must be Base64 encoded. **ClientID MUST match the ClientID used in step 2 and ClientSecret must be the correct one for the ClientID (see Valid Clients table above).**

            - Request body:
            > redirect_uri={RedirectURI}&grant_type=authorization_code&code={AuthorizationCode}

            - Parameters:
                - {RedirectURI}: Client Application's redirect URI. **URI must be URL-encoded.**
                - {AuthorizationCode}: the Authorization Code retrieved from last step
                
            - Response body format as below, {AuthAccessToken} is the token string:
            > {"expires_in":28800,"token_type":"Bearer","access_token":"{AuthAccessToken}"}
        6. Client Application invokes IR Gateway Services with the OAuth Access Token in header
            - Url format:
            > http://{ServiceHostdomain}/gateway/GWS/Returns
			
			- Parameters:
                - {ServiceHostdomain}: this is IR's gateway service environment specific domain that is accessed after your endpoint IP / CIDR range is white-listed. 
            - Request headers MUST include:
            > Authorization: Bearer {AuthAccessToken}            
            - Request body is the actual service payload (please refer the request samples **#link**)
			
Sample curl commands:
----------------- 
	- Steps to test the OAuth Flow
		- Url format:
            > http://{ServiceHostdomain}/{endpoint_actions}
			
	- Parameters:
			- {ServiceHostdomain}: this is IR's gateway service environment specific domain that is accessed after your endpoint IP / CIDR range is white-listed.
		1. ** Request Auth Code **
				- curl -v 'https://{ServiceHostdomain}/ms_oauth/oauth2/endpoints/oauthservice/authorize?client_id=TestClient1&redirect_uri=https://testpartner.ird.services/&scope=MYIR.Services&response_type=code' -c cookie.txt -D cookie_header.txt
			- The above command writes out the session cookie to cookie.txt and its header to cookie_header.txt. Both of these files are used in the next command
        2. ** Get Auth Code **
				- curl -v -X POST https://{ServiceHostdomain}/oam/server/auth_cred_submit -H 'content-type: application/x-www-form-urlencoded' -d 'userid=userid&password=password&login=Login' -b cookie.txt -c cookie.txt -D cookie_header.txt	
			- The above command outputs the authorization_code as 'code=' onto the stdout/terminal in two places (1 or 2 like below) which needs to be used in the next command
		3.  ** Get Auth Token **
				- curl -v -X POST 'https://{ServiceHostdomain}/ms_oauth/oauth2/endpoints/oauthservice/tokens' -H 'content-type: application/x-www-form-urlencoded' -H 'Authorization: Basic VGVzdENsaWVudDE6VGVzdENsaWVudDFTZWNyZXQ=' -d 'redirect_uri=https%3A%2F%2Ftestpartner.ird.services%2F&grant_type=authorization_code&code={CODE_FROM_ABOVE_COMMAND}' -o token.txt
			- The above command writes out the authentication token to token.txt. The token is used in GWS requests like the one below. The authorization header in the above command is the ClientId and ClientSecret base64 encoded.
		4. ** API call to Smoke Test EI (Prepop Operation) **
				- curl -X POST 'https://{ServiceHostdomain}/gateway/GWS/Returns' -H 'Authorization: Bearer {TOKEN_FROM_ABOVE_COMMAND}' -H 'Content-Type: application/x-www-form-urlencoded' -d @prepoprequest.xml
			- Authorization token is from the token.txt file in the previous step and prepoprequest.xml is from sample payload.