OAuth 2.0, which stands for “Open Authorization”, is a standard designed to allow a website or application to access resources hosted by other web apps on behalf of a user.

OAuth2.0 has 4 roles : 

1) Resource Owner: The user or system that owns the protected resources and can grant access to them.

2) Client: The client is the system that requires access to the protected resources. To access resources, the Client must hold the appropriate Access Token.

3) Authorization Server: This server receives requests from the Client for Access Tokens and issues them upon successful authentication and consent by the Resource Owner. The authorization server exposes two endpoints: the Authorization endpoint, which handles the interactive authentication and consent of the user, and the Token endpoint, which is involved in a machine to machine interaction.

4) Resource Server: A server that protects the user’s resources and receives access requests from the Client. It accepts and validates an Access Token from the Client and returns the appropriate resources to it.


OAuth allows granular access levels. Rather than entrusting our entire protected data to a third party, we would prefer to share just the necessary data with them. Thus, we need a trusted intermediary that would grant limited access(known as scope) to the editor without revealing the user’s credentials once the user has granted permission.(known as consent).

![image](https://github.com/Pushkariiit/OAuth2.0-Implementation/assets/96918138/47e5681f-6c36-404f-b67c-d0b0d647c4e7)

Lets take an example on the implementation of OAuth2.0


![image](https://github.com/Pushkariiit/OAuth2.0-Implementation/assets/96918138/87504551-7736-4a53-9eec-fdcc0ad6b35b)


So here : 
Resource Owner  : Google (Bcoz it has all the resources of user)
Client : Me
Authorization server : 
Resource server : Google server

Grant Types of OAuth: 
1) implicit
2) authorization code
3) resource owner password credential
4) client credential

Let’s see how authorization code works ?

So on Zomato page we click on sign with google it generates REQUEST (GET) , this request is passed to Authorization server.
Authorization server grants permission and sends : 
response_type : code,Client_id,Redirect_url, scope,state
This request is called AuthGrant 
Now zomato wants the email id of client which is available of resource server (i.e. google) but resource server requires access tokens. To get access token zomato website again make request to authorization server using the earlier got response_type  (also grant_type,client_id,client_secret,redirect_url) and then authorization server provides 
Access token and then zomato server gives access token to resource server and client is signed in.
