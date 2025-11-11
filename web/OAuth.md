# Resource owner
a resource owner is a person or system that controls certain data and can authorise an application to access that data on their behalf
# Client
The client can be a mobile app or a server-side web application. It acts as an intermediary, requesting access to resources and performing actions as permitted by the resource owner
# Authorisation server
The authorisation server is responsible for issuing tokens to the client after successfully authentication the resource owner and obtaining their authorisation. The authorisation server plays a crucial role in the OAuth process by ensuring the client is granted permission only after legitimate user authentication and consent
# Resource server
The server hosting protected resources can accept and respond to protected resource requests using access tokens. This server ensures that only authenticated and authorised clients can access or manipulate the resource owner's data
# Authorisation grant
The client uses a credential representing the resource owner's authorisation to obtain an access token. The primary grant types are: authorisation code, implicit, resource owner password credentials, and client credentials
# Access token
A credential that the client can use to access protected resources on behalf of the resource owner. It has a limited lifespan and scope. Access tokens are essential for maintaining secure and protected communications between the client and resource server without repeatedly asking the resource owner for credentials
# Refresh token
A credential that the client can use to obtain a new access token without requiring the resource owner to re-authenticate. Refresh tokens are typically long-lived and provide a way to maintain user sessions without frequent login interruptions
# Redirect URI
The URI to which the authorisation server will redirect the resource owner's after a grant or denial of the authorisation
# State parameter
An optional parameter maintains the state between the client and the authorisation server. it can help prevent cross site request forgery by ensuring the response matches the client's request
# Grant types
## Authorisation code grant
This gran is the most commonly used OAuth 2.0 flow suited for server-side applications. In this flow, the client redirects the user to the authorisation server, where the user authenticates and grants authorisation. The authorisation server then redirects the user to the client with an authorisation code. The client exchanges the authorisation code for an access token by requesting the authorisation server's token endpoint. This grant type is known for its enhanced security, as the authorisation code is exchanged for an access token server-to-server, meaning the access token is not exposed to the user agent. It also supports using refresh tokens to maintain long-term access without repeated user authentication
## Implicit grant
The implicit grant is primarily designed for mobile and web applications where clients cannot securely store secrets. It directly issues the access token to the client requiring an authorisation code exchange. In this flow, the client redirects the user to the authorisation. After the user authenticates and grants authorisation, the authorisation server returns an access token in the url fragment. This is less secure than Authorisation code grant, however is less secure as the access token is exposed to the user agent and can be logged in the browser history. it also does not support refresh tokens
## Resource owner password credentials grant
The resource owner password credentials grant is used when the client is highly trusted by the resource owner, such as first-party applications. The client collects the users credential directly and exchanges them for an access token. This grant type is direct, requiring fewer interactions, making it suitable for highly trusted applications where the user is confident in providing their credentials
## Client credential grant
The client credential grant is used for server to server interaction without user involvement. The client uses his credentials to authenticate with the authorisation server and obtain an access token. In this flow, the client authenticates with the authorisation server using its client credentials, and the authorisation server issues access tokens directly to the client