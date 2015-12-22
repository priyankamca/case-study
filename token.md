#TOKEN BASED AUTHENTICATION
 
  #Need for token based:

        Server Based Authentication (The Traditional Method)

            In olden days,this is used since the HTTP protocol is stateless, this means that if we authenticate        a user with a username and password, then on the next request, our application won’t know who we are.          We would have to authenticate again.The main problem arise was in session,scalability,Cross Origin             Resource Sharing etc.,.

            So we move onto token based authentication.

   #Token Based:
  
            Token-based authentication can be considered a specialized version of Basic Authentication. The           Authorization header tag will contain the auth token as the username, and no password.This script
       assumes that user accounts are stored in an DB. All API resources/methods will be secured unless they          are made explicitly public.
 
          It is enabled by retrieving the user auth token by performing an HTTP POST with the authentication   
  details as JSON data against the authentication endpoint. A successful call to this endpoint will return the      user’s ID and their authentication token.This token can be used in subsequent requests to protected resources.


     Working:
     -------
          Token based authentication is stateless. We are not storing any information about our user on the
     server or in a session.This concept alone takes care of many of the problems with having to store
     information on the server.                

              1.  User Requests Access with Username / Password
              2.  Application validates credentials
              3.  Application provides a signed token to the client
              4.  Client stores that token and sends it along with every request
              5.  Server verifies token and responds with data
      
     Benefits:
     --------
               Stateless and Scalable: Tokens stored on client side. Completely stateless, and ready to be scaled.

               Security: The token also expires after a set amount of time, so a user will be required to login once again. This helps us stay secure. There is also the concept of token revocation that allows us to invalidate a specific token and even a group of tokens based on the same authorization grant.

               Extensibility: Tokens will allow us to build applications that share permissions with another.

               Multiple Platforms and Domains: Our data and resources are available to requests from any domain now as long as a user has a valid token.

               Standards Based: When creating the token, you have a few options but the standard to use would be JSON Web Tokens.This handy debugger and library chart shows the support for JSON Web Tokens.

     Solution:
  
          A generic token is a random string; the server keeps in its database a mapping from emitted tokens to authenticated user names. Old tokens can be removed automatically in order to prevent the servers database from growing indefinitely. Such a token is good enough for security as long as an attacker cannot create a valid token with non-negligible probability, a "valid token" being "a token which is in the database of emitted tokens". It is sufficient that token values have length at least 16 bytes and are produced with a cryptographically strong PRNG

          The token

		must be allowed to be used only once,
		must only be usable for the user it was created for,
		must only be sent via HTTPS,
		should have an expiry date (e.g. 7 days).
	    Once the user logs in with the token, it is invalid and a new token should be created and given to the user. In the case of an expired token, the user must be made to log in again, using their real credentials.
  

  #Implementation:

      There are many ways to implement tokens. A straightforward implementation is to generate a random sequence of characters of certain length that is stored with the user and the password in the database, possibly with an expiration date as well. The token then becomes sort of a plain text password, in that can be easily verified with a string comparison, plus a check of its expiration date.

      A more elaborated implementation that requires no server side storage is to use a cryptographically signed message as a token. This has the advantage that the information related to the token, namely the user for which the token was generated, is encoded in the token itself and protected against tampering with a strong cryptographic signature.

    

   
  
  

 
