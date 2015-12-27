OPEN AUTHENTICATION:

   #OAuth definition:

       OAuth (Open Authorization) is an open standard for token-based authentication and authorization on the Internet.OAuth, which is pronounced "oh-auth," allows an end user's account information to be used by third-party services, such as Facebook, without exposing the user's password. OAuth acts as an intermediary on behalf of the end user, providing the service with an access token that authorizes specific account information to be shared. The process for obtaining the token is called a flow.

   Workings:
   
        1.The user accesses the client web application. In this web app is button saying "Login via Facebook"
        2.when the user clicks the login button, the user is redirected to the authenticating application.The user then logs into the authenticating application, and is asked if she wants to grant access to her data in the authenticating application, to the client application. The user accepts.
        3.The authenticating application redirects the user to a redirect URI, which the client app has provided to the authenticating app.
        4.The user accesses the page located at the redirect URI in the client application. In the background the client application contacts the authenticating application and sends client id, client password and the authentication code received in the redirect request parameters. The authenticating application sends back an access token.
        5.Once the client application has obtained an access token, this access token can be sent to the Facebook, Google, Twitter etc. to access resources in these systems, related to the user who logged in.

   Request and Response:

	When the client application requests authorization and access tokens it sends HTTP requests to the authorization server, to its authorization and token endpoints. What request and response is sent forth and back depends on the authorization grant type. Remember, the four grant types are:

		1.Authorization Code Grant:
                            The authorization request is sent to the authorization endpoint to obtain an authorization code. The authorization response contains the authorization code needed to obtain an access token. 
		2.Implicit Grant:
                            The implicit grant consists of only 1 request and 1 response.
  		3.Resource Owner Password Credentials Grant:
                            The resource owner password credentials authorization contains a single request + response.The response is a JSON structure containing the access token. 
		4.Client Credentials Grant.

   Benefit:
              1.Ease.
              2.Networking.
              3.Time.
              4.Privacy
              5.Security.
              6.COntrol.
              7.Popularity.

  Implementation:

         If we use OAuth in code we first import the provider like below,

                 app.config.update({
                   'OAUTH1_PROVIDER_ENFORCE_SSL': False,
                   'OAUTH1_PROVIDER_KEY_LENGTH': (10, 100),
                  })

                Because we are developing on a local machine, it would be easier for us to implement it over HTTP.        

                 from flask_oauthlib.provider import OAuth1Provider
                 oauth = OAuth1Provider(app)


    
	



