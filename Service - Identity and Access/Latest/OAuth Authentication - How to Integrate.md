![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# OAuth Authentication - How to Integrate

#### Table of contents:

* [Simulating Authentication Flow](#simulating-authentication-flow)
* [Full Authentication Steps](#full-authentication-steps)
    * Step 1. Service Request  
    * Step 2. Request Login Page
    * Step 3. Submit Login Credentials
    * Step 4. Redirect to Client Application
    * Step 5. Exchange Authorization Code for an Access Token

<a name="simulating-authentication-flow"/>

## Simulating Authentication Flow:
	
High Level Flow
![High Level Flow](images/high_level_flow.jpg)
	
Sequence Diagram
![Sequence Diagram](images/sequence_diagram.png)

<a name="full-authentication-steps"/>

## Full Authentication Steps:

In our gateway services environments OAuth service is used, so as a service provider you would need to trigger customer's behaviour to complete this OAuth flow.

### Step 1. Service Request 
Customer accesses the Client Application via a browser. They take an action that requires access to myIR Gateway Services.

### Step 2. Request Login Page
The Client Application invokes the OAuth Server to get access token, the customer's browser is redirected to myIR login page.
	At this step as a service provider you need to send a ```HTTP GET``` request to OAuth Server, URL format as below:

```http
https://{ServiceHostdomain}:{AuthServicePort}/ms_oauth/oauth2/endpoints/oauthservice/authorize
?client_id={ClientID}
&redirect_uri={RedirectURI}
&scope=MYIR.Services
&response_type=code
&state={State}
```
 
Parameters:
* ```{ClientID}``` a valid client identifier, see [Valid Clients](#mock-valid-clients) table below
* ```{RedirectURI}``` Client Application's redirect URI
* ```{State}``` **Optional, but recommended** e.g. GUID, random string value created by the Client Application as a method of maintaining state. 
			
### Step 3. Submit Login Credentials
User submits credentials and autothorise consent -  At this step the Client Application will need to send a ```HTTP POST``` request to OAuth Server.

>Note:
>
> * **The consent page and redirection pages are skipped in this mock environment (emulated service).**
> * **For the Test and Production environements, the onboaring team will provide you with your Client ID and Client Secret.**

#### URL format:
```http 
https://{ServiceHostdomain}/oam/server/auth_cred_submit
```
		
Parameter:
* ```{ServiceHostdomain}```: this is IR's gateway service environment specific domain that is accessed after your endpoint IP / CIDR range is white-listed. 

>Note:
>
>The production environmnet does not require IP address whitelisting.
		
**HTTP POST** Request headers MUST include:
```http 
Content-Type: application/x-www-form-urlencoded
Cookie: {CookieFromLastStep}
```
		
Request HTTP header and body: 
```http 
POST /oam/server/auth_cred_submit HTTP/1.1
Host: {ServiceHostdomain} 
Cookie: {CookieFromLastStep}
Content-Type: application/x-www-form-urlencoded

userid={CustomerUserID}
&password={CustomerUserPassword}
&login=Login
```

Parameters:
<a name="MockValidClients" />        
* ```{CustomerUserID}``` myIR User ID
* ```{CustomerUserPassword}``` myIR Password

### Step 4. Redirect to Client Application
Authorization Code returns to Client Application by a ```HTTP 302 redirection``` to the ```{redirectURI}```.

#### Response URL Format:
```http
https://{RedirectURI}?code={AuthorizationCode}&state={State}
```

Parameters:
* ```{RedirectURI}``` Client Application's redirect URI
* ```{AuthorizationCode}``` The Authorization Code to be used for retrieving an access token	
* ```{State}``` The matching string value which was origninally created by the Client Application 

### Step 5. Exchange Authorization Code for an Access Token
Client Application retrieves OAuth Access Token by submits a ```HTTP POST``` request using the Authorization Code as well as client application's credentials

#### URL Format:
```http
https://{ServiceHostdomain}/ms_oauth/oauth2/endpoints/oauthservice/tokens
```
		
Parameters:
* ```{ServiceHostdomain}```: this is IR's gateway service environment specific domain that is accessed after your endpoint IP / CIDR range is white-listed.
* ```{ClientApplicationEncodedCredentials}```: the encoded client application's credentials, must be Base64 encoded. 

>Note:
>
>Request HTTP header must include:
>  ```http
>  Authorization: Basic {ClientApplicationEncodedCredentials}
>  Content-Type: application/x-www-form-urlencoded
>  ``` 

Parameters:


#### Request HTTP header and body: 
```http 
POST /ms_oauth/oauth2/endpoints/oauthservice/tokens HTTP/1.1
Host: {ServiceHostDomain}
Content-Type: application/x-www-form-urlencoded
Authentication: Basic {ClientApplicationEncodedCredentials}

redirect_uri={RedirectURI}
&code={AuthorizationCode}
&grant_type=authorization_code
```

Parameters:
* ```{RedirectURI}```: Client Application's redirect URI. **URI must be URL-encoded.**
* ```{AuthorizationCode}```: the Authorization Code retrieved from last step

Response HTTP Header and body format as below: 
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "expires_in":28800,
    "token_type":"Bearer",
    "access_token":"{AuthAccessToken}"
}
```
Parameters:
* ```{AuthAccessToken}```: is the access token string value which is then used in consuming the Gateway Services. 