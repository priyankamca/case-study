# case-study

0 Session based authentication
1 Token based authentication
2 Persistent Storage
3 RESTful Design pattern
4 Open authentication
5 Editor


#Authentication:

                 Authentication is the mechanism whereby systems may securely identify their users.It is the process of actually confirming that identity such as identity documents, digital certificate.

   Authentication schemes: 
                1.    Basic Authentication.
                11.  Token Authentication.
                111. HMAC Authentication.
    
     1.Basic Authentication:
                 This script assumes that user accounts are stored in an accounts DB
      collection, and that passwords are stored as bcrypt hashes. All API
      resources/methods will be secured unless they are made explicitly public.             
  
     11.Token Authentication:
                  The Authorization header tag will contain the auth token as the username,
      and no password.This script assumes that user accounts are stored in an accounts
      DB collection. All API resources/methods will be secured unless they are made
      explicitly public.

     111. HMAC Authentication.
                   HMAC (Hash Message Authentication Code) authentication, which is 
      basically a very secure custom authentication scheme built around the
      authorization header.
                   The server provides the client with a user id and a secret key through 
      some out-of-band technique (e.g., the service sends the client an e-mail
      containing the user id and secret key). The client will use the supplied secret key 
      to sign all requests.

#Session:
     A session is a way to store information (in variables) to be used across multiple
 pages.A session is set up for  a certain point in time.

  #Session management:
         It is the process of keeping track of a user's activity across sessions of interaction with the computer system.There are desktop,browser,webserver session managements.

  **Desktop :
            A desktop session manager is a program that can save and restore desktop sessions.
  **Browser:
            In a web browser where a user can save all open pages and settings and restore them at a later date.
  **Webserver:
            The web server  cannot rely on TCP network connection for longer than a single HTTP GET or POST operation. Session management is the technique used by the web developer to make the stateless HTTP protocol support session state. 
  
  #Server-side session:
           A method of using server-side sessions in systems without mass-storage is to reserve a portion of RAM for storage of session data. This method is applicable for servers with a limited number of clients.


# Solution:
     A session token is a unique identifier that is generated and sent from a server to a client  to identify the current interaction session.The client only has to handle the identifier all session data is stored on the server(database) linked to that id.The client doesnot have access directly.

#Implementation:
     Sessions variables are stored client side, on the users browser the content of the variables is encrypted, so users can't actually see it. They could edit it, but again, as the content wouldn't be signed with this hash key, it wouldn't be valid.You need to set a scret key (random text) and keep it secret.
     app.secret_key = 'F12Zr47j\3yX R~X@H!jmM]Lwf/,?KT'

     Define a route for the main page.Form route - Will show a form where the user can set its name and will be set as a session variable. This route will clear the variable sessions.This functionality can come handy for example when we logout a user from our app and we want to clear its information.

