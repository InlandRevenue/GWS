![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

# OAuth Authentication - How to Integrate

#### Table of contents:

* [Simulating Authentication Flow](#simulating-authentication-flow)
* [Full authentication steps](#full-authentication-steps)
    * Issuing OAuth Access Token
    * Validating OAuth Access Token
* [Sample cURL commands](#sample-curl-commands)
    * Request OAuth Code
	* Submit Client Credentials
	* Get OAuth Token 
	* API call to Smoke Test (Prepop Operation)

<a name="simulating-authentication-flow"/>

## Simulating Authentication Flow:
	
High Level Flow
![High Level Flow](images/high_level_flow.jpg)
	
Sequence Diagram
![Sequence Diagram](images/sequence_diagram.png)

<a name="full-authentication-steps"/>

## Full authentication steps:

In our gateway services environments OAuth service is used, so as a service provider you would need to trigger customer's behaviour to complete this OAuth flow.

**1.** Customer accesses the Client Application via browser. They take an action that requires access to IR Gateway Services.

**2.** The Client Application invokes the OAuth Server to get access token, the customer's browser is redirected to IR login page.
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
<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
* ```{State}``` **Recommended** e.g. GUID, random string value created by the Client Application
=======
* ```{State}``` **Recomended** e.g. GUID, random string value created by the Client Application
>>>>>>> 15a8e8d42d1ec8da3bee244c66b8d8d1aca1d859
=======
* ```{State}``` **Recomended** e.g. GUID, random string value created by the Client Application
>>>>>>> 15a8e8d42d1ec8da3bee244c66b8d8d1aca1d859
=======
* ```{State}``` **Recomended** e.g. GUID, random string value created by the Client Application
>>>>>>> 15a8e8d42d1ec8da3bee244c66b8d8d1aca1d859
			
<a name="mock-valid-clients"/>        

### Valid Clients - in Mock Services Environment:
| Client ID | Client Secret | Valid User|
|-|-|:--:|
| ```TestClient1``` | ```TestClient1Secret``` | yes |
| ```TestClient2``` | ```TestClient2Secret``` | no |
			
**3.** User login to MyIR and consent - Customer submits credentials. At this step as a service provider you need to send a ```HTTP POST``` request to OAuth Server.

>Note:
>
> * The consent page and redirection pages are skipped in this emulated service.
<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
> * The Testing & Production environments, the on-boarding team will provide you with your Client ID and Client Secret.
=======
> * The Testing & Production environements, the onboaring team will provide you with your Client ID and Client Secret.
>>>>>>> 15a8e8d42d1ec8da3bee244c66b8d8d1aca1d859
=======
> * The Testing & Production environements, the onboaring team will provide you with your Client ID and Client Secret.
>>>>>>> 15a8e8d42d1ec8da3bee244c66b8d8d1aca1d859
=======
> * The Testing & Production environements, the onboaring team will provide you with your Client ID and Client Secret.
>>>>>>> 15a8e8d42d1ec8da3bee244c66b8d8d1aca1d859

### URL format:
```http 
https://{ServiceHostdomain}/oam/server/auth_cred_submit
```
		
Parameter:
* ```{ServiceHostdomain}```: this is IR's gateway service environment specific domain that is accessed after your endpoint IP / CIDR range is white-listed. 
		
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
* ```{CustomerUserID}``` **can be anything for clients that have users (see [Valid Clients](#mock-valid-clients) table above).**
* ```{CustomerUserPassword}``` **can be anything for clients that have users (see [Valid Clients](#mock-valid-clients) table above).**	

**4.** Authorization Code returns to Client Application by a ```HTTP 302 redirection``` to the redirectURI.

Response URL Format:
```http
https://{RedirectURI}?code={AuthorizationCode}&state={State}
```

Parameters:
* ```{RedirectURI}``` Client Application's redirect URI
* ```{AuthorizationCode}``` the Authorization Code to be used for retrieving an access token	
<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
* ```{State}``` **Recommended** e.g. GUID, random string value created by the client application 
=======
* ```{State}``` **Recomended** e.g. GUID, random string value created by the client application 
>>>>>>> 15a8e8d42d1ec8da3bee244c66b8d8d1aca1d859
=======
* ```{State}``` **Recomended** e.g. GUID, random string value created by the client application 
>>>>>>> 15a8e8d42d1ec8da3bee244c66b8d8d1aca1d859
=======
* ```{State}``` **Recomended** e.g. GUID, random string value created by the client application 
>>>>>>> 15a8e8d42d1ec8da3bee244c66b8d8d1aca1d859

**5.** Client Application retrieves OAuth Access Token by sending Authorization Code as well as client application's credentials

URL Format:
```http
https://{ServiceHostdomain}/ms_oauth/oauth2/endpoints/oauthservice/tokens
```
		
Parameters:
* ```{ServiceHostdomain}```: this is IR's gateway service environment specific domain that is accessed after your endpoint IP / CIDR range is white-listed.

Request HTTP header MUST include:
```http
Authorization: Basic {ClientApplicationEncodedCredentials}
Content-Type: application/x-www-form-urlencoded
``` 

Parameters:
* {ClientApplicationEncodedCredentials}: the encoded client application's credentials, must be Base64 encoded. 

Request HTTP header and body: 
```http 
POST /ms_oauth/oauth2/endpoints/oauthservice/tokens HTTP/1.1
Host: {ServiceHostDomain}
Content-Type: application/x-www-form-urlencoded
Authentication: Basic {ClientApplicationEncodedCredentials}

redirect_uri={RedirectURI}
&code={AuthorizationCode}
&grant_type=authorization_code
```

>Note:
> 
>For the mock environment the Client ID MUST match the Client ID used in step 2 and Client Secret must be the correct one for the Client ID (see [Valid Clients](#mock-valid-clients) table above).

Parameters:
* ```{RedirectURI}```: Client Application's redirect URI. **URI must be URL-encoded.**
* ```{AuthorizationCode}```: the Authorization Code retrieved from last step

Response HTTP Header and body format as below, ```{AuthAccessToken}``` is the token string:
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "expires_in":28800,
    "token_type":"Bearer",
    "access_token":"{AuthAccessToken}"
}
```
___

Client Application invokes IR Gateway Services with the OAuth Access Token in HTTP header. 

URL format for native desktop based application:
```http
https://{ServiceHostdomain}/gateway2/gws/returns/
```

URL format for cloud based application:
```http
https://{ServiceHostdomain}:4046/gateway/gws/returns/
```   

Parameters:

* ```{ServiceHostdomain}``` this is IR's gateway service environment specific domain that is accessed after your endpoint IP / CIDR range is white-listed. 

> Note: 
>* Request headers MUST include: ```Authorization: Bearer {AuthAccessToken}``` 
>* Request body is the actual service payload

<a name="sample-curl-commands"/>

## Sample cURL commands

#### Request Auth Code:

```php
curl -v 'https://{ServiceHostdomain}/ms_oauth/oauth2/endpoints/oauthservice/authorize?client_id=TestClient1&redirect_uri=https://testpartner.ird.services/&scope=MYIR.Services&response_type=code' -c cookie.txt -D cookie_header.txt
```

The above command writes out the session cookie to cookie.txt and its header to cookie_header.txt. Both of these files are used in the next command.
		
#### Submit Client Credentials:

```php
curl -v -X POST 'https://{ServiceHostdomain}/oam/server/auth_cred_submit' -H 'content-type: application/x-www-form-urlencoded' -d 'userid=userid&password=password&login=Login' -b cookie.txt -c cookie.txt -D cookie_header.txt
```	

The above command outputs the authorization_code as ```code=``` onto the stdout/terminal which is needed to be used in the next command.
		
#### Get Auth Token:
```php
curl -v -X POST 'https://{ServiceHostdomain}/ms_oauth/oauth2/endpoints/oauthservice/tokens' -H 'content-type: application/x-www-form-urlencoded' -H 'Authorization: Basic VGVzdENsaWVudDE6VGVzdENsaWVudDFTZWNyZXQ=' -d 'redirect_uri=https%3A%2F%2Ftestpartner.ird.services%2F&grant_type=authorization_code&code={CODE_FROM_ABOVE_COMMAND}' -o token.txt
```

The above command writes out the authentication token to ```token.txt```. The token is used in GWS requests like the one below. The authorization header in the above command is the Client ID & Client Secret Base64 Encoded.
		
#### API call to Smoke Test Return Service (Prepop Operation)

##### Native Desktop Application:
```php
curl -X POST 'https://{ServiceHostdomain}/gateway2/GWS/Returns/' -H 'Authorization: Bearer {TOKEN_FROM_ABOVE_COMMAND}' -H 'Content-Type: application/soap+xml' -d @prepoprequest.xml
```
##### Cloud Application (testing & production environments only):
```php
curl -E {PartnersCert} --key {PartnersKey} -X POST 'https://{ServiceHostdomain}:4046/gateway/GWS/Returns/' -H 'Authorization: Bearer {TOKEN_FROM_ABOVE_COMMAND}' -H 'Content-Type: application/soap+xml' -d @prepoprequest.xml
```

Parameters:
* ```{PartnersCert}``` Client certificate file
* ```{PartnersKey}```  Private key file name

>Note:
>
>Authorization Access Token is from the ```token.txt``` file in the previous step and prepoprequest.xml is from sample payload.