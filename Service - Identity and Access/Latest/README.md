![IRD logo](../../Images/IRlogo.gif)
![Software Dev](../../Images/SoftwareDev.png)

Identity and Access Service
=======================================

Key Features:
-------------

* [View and download the Identity and Access Service Build Pack](Build%20pack%20-%20Identity%20and%20Access%20Services.pdf) for details on 
	- the token auth implementation using OAuth 2.0
	- desktop (native) application token auth 
	- SSH Keys

* OAuth Authentication - [How to Integrate](OAuth%20Authentication%20-%20How%20to%20Integrate.md)

* Message Samples - OAuth requests and responses
	- Authorisation code request and response
	- Access token request and response
	- Refresh token request and response
	- Validate token request and response
	- Revoke token request and response
	- Error response	

		
Message Samples - OAuth requests and responses
-----------------------

- OAuth requests and responses

    1. Request Authorisation Code : Service consumer to IR
		- Request sample
			- Service provider will send a HTTP GET request to Auth Server, 
			  Url format
			  > https://q.services.ird.govt.nz/ms_oauth/oauth2/endpoints/oauthservice/authorize?client_id=Test99999999&redirect_uri=https://myreturnuri/test/&scope=MYIR.Services&response_type=code
	2. Authorisation Code response : IR to Service consumer
		- Response sample
			- Url format
			  > https://myreturnuri/test/?code=eyJhbGciOiJSUzUxMiIsInR5cCI6IkpXVCIsIng1dCI6Ino5VFR1R2pHSVJNd01pQjRaUGxjbzhDZ3JlOCIsImtpZCI6Im9yYWtleSJ9.eyJvcmFjbGUub2F1dGgucmVkaXJlY3QtdXJpIjoiaHR0cHM6Ly9qZW5raW5zLmtpd2lzYXZlci5pcmQuZGlnaXRhbHBhcnRuZXIuc2VydmljZXMvIiwic3ViIjpudWxsLCJvcmFjbGUub2F1dGgudXNlcl9vcmlnaW5faWRfdHlwZSI6IkxEQVBfVUlEIiwib3JhY2xlLm9hdXRoLnVzZXJfb3JpZ2luX2lkIjoic2FtbXkzOTAiLCJpc3MiOiJJbmxhbmRSZXZlbnVlIiwib3JhY2xlLm9hdXRoLnN2Y19wX24iOiJPQXV0aFNlcnZpY2VQcm9maWxlIiwiaWF0IjoxNTAyMzIxNDI3LCJvcmFjbGUub2F1dGgudGtfY29udGV4dCI6ImF6YyIsImV4cCI6MTUwMjM1MDIyNywicHJuIjpudWxsLCJqdGkiOiJhNDg2ZTU1Ny0zZTc1LTQ3ZmYtODk0NC1hNTcxZWNlYzgzNmYiLCJvcmFjbGUub2F1dGguc2NvcGUiOiJNWUlSLlNlcnZpY2VzIiwib3JhY2xlLm9hdXRoLmNsaWVudF9vcmlnaW5faWQiOiJUZXN0MzAyMDY0OTIiLCJ1c2VyLnRlbmFudC5uYW1lIjoiRGVmYXVsdERvbWFpbiIsIm9yYWNsZS5vYXV0aC5pZF9kX2lkIjoiMTIzNDU2NzgtMTIzNC0xMjM0LTEyMzQtMTIzNDU2Nzg5MDEyIn0.NTBu3R-JwaaOWfvMdWAHqY7Ji3YI3I-bSTXqx6jauqEUhswLmAG6cbpGaSky50ECbHNv2skU8WVZ0RYv67KPgITGXJz0ZKSjqOgiZ0R4kFCZ7asN8yjIzXgxwWk4mPXL5E02u24-VMbr_hrNZYDZbakOpz4uY6UlSSNECmw0ac8
		- [Success Response sample – Authorisation Code sent](sample_messages/authorisation-code-response.txt)
		
    3. Request Access token : Service consumer to IR
		- Exchange Authorisation Code for oAuth Access Token
			At this step as a service provider you need to send a HTTP POST request to Auth Server with Authorization Code and your client credentials
			Url format:
			> https://q.services.ird.govt.nz/ms_oauth/oauth2/endpoints/oauthservice/tokens
				- [request sample header](sample_messages/access-token-requestheader.txt)
				- [request sample body](sample_messages/access-token-requestbody.txt)
		
		- Success Response – Access Token sent
		The response contains the Access Token and expiry time.
			- [response sample](sample_messages/access-token-response.txt)
		
		If refresh tokens are used this is also returned
			- [response sample with refresh](sample_messages/access-token-refresh-token-response.txt)
		
    4. Request Refresh token : Service consumer to IR
		- Refresh request
			At this step as a service provider you need to send a HTTP POST request to the Auth Server with the Refresh Token and your client credentials
			- [request sample header](sample_messages/refresh-token-requestheader.txt)
			- [request sample body](sample_messages/refresh-token-requestbody.txt)

		- Refresh token reply
			The Refresh token reply is the same as an authorisation code exchange for an Access token
			- [response sample](sample_messages/refresh-token-reply.txt)
    
	5. Error response
			- [response sample](sample_messages/error-response.json)
	
	6. Validate token request : Service consumer to IR
		- Validate token request 
			As a service provider you need to send a HTTP POST request to Auth Server with Access Token to validate your client credentials
			Url format:
			> https://q.services.ird.govt.nz/ms_oauth/oauth2/endpoints/oauthservice/tokens
				- [request sample header](sample_messages/validate-token-requestheader.json)
				- [request sample body](sample_messages/validate-token-requestbody.json)

		- Validate  token reply 
			- [response sample](ssample_messages/validate-token-response.json)
			- [error response sample](ssample_messages/validate-token-error-response.json)
    
	7. Revoke token request : Service consumer to IR
		- Revoke token request 
			At this step as a service provider you need to send a HTTP POST request to Auth Server with Access Token OR Refresh Token to revoke your client credentials. 
			- Url format:
			> https://q.services.ird.govt.nz/ms_oauth/oauth2/endpoints/oauthservice/tokens
				- [request sample header](sample_messages/revoke-token-requestheader.json)
				- [request sample body](sample_messages/revoke-token-requestbody.json)
		
		- Revoke token reply 
			- [response sample](sample_messages/revoke-token-response.json)
			- [error response sample](sample_messages/revoke-token-error-response.json)