Inherently HTTP(S) is stateless therefore to keep track of the user, HTTP(S) uses sessions
# Lifecycle of a session
## Session creation
When you initially visit a web application you create a session immediately (in some cases) so that the application can track your actions before you authenticated
### Vulnerabilities
#### Weak session values
It is less common to see weak session values in modern times as frameworks are consistently used. However with the rise of LLMs and other AI code-assistant solutions, you would be surprised at how often these old-school vulnerabilities are creeping back in
#### Controllable session values
In certain tokens, such as JWTs, all relevant information to both create and verify the JWT's validity is provided. If security measures are not enforced, such as verifying the token's signature, or ensuring that the signature itself was created securely, a thread actor would be able to generate their own token
#### Session fixation
Web applications that give you a session before authentication can be vulnerable to session fixation. If your session value is not adequately rotated when you authenticate, a suitably positioned threat actor could record it and use it when your authenticated
#### Insecure session transmission
In modern environments, it is common for the authentication server and the application servers to be distinct. In order for this to work, your session must be transferred from the authentication server to the application server via your browser. In this transmission, however, certain issues can creep in that would expose your session information to a threat actor
## Session tracking
Once you receive a session token, this is submitted with every new request. This allows the web application to track your progress through the application, it can use a server side lookup to cross-reference who made the request and what permissions they have
### Vulnerabilities
#### Authorisation bypass
Authorisation bypasses occur when there aren't sufficient checks being performed on whether a user is allowed to perform the action they requested. In essence, this fails to track the user's session and its associated rights correctly:
- Vertical bypass - you can perform an action that is reserver for a more privileged user
- Horizontal bypass - you can perform an action you are allowed to perform, but on a dataset you should not be able to perform on
#### Insufficient logging
A key issue during some incidents is not having sufficient information to piece together an attack. While a lot of logging will occur at an infrastructure level, application logging can be crucial to understanding what went wront
## Session expiry
Incase you close your browser or tab the application has no way of knowing that you closed it, this is why sessions have a lifetime and if you submit an old session value to a web application, it should be denied as the session should have been expired
## Session termination
In some cases the user might forcibly perform a logout action. In the even that this occurs, the web application should terminate the user's session. While similar to session expiry, it is unique in the sense that even if the session's lifetime is still valid the session itself should be terminated
### Vulnerabilities
#### Server and client de-sync
When clicking a logout button the client side cookie will be removed, but sometimes they may forget to remove it server side, this may indicate you could use other users tokens from being logged out
# IAAA
## Identification
identification is the process of verifying who the user is. This starts with the user claiming to be a specific identity
## Authentication
Authentication is the process of ensuring that the user is who they say they are, this requires you provide proof that you are who you say you are, this could be a password for example, this is the point where session creation would kicking by
## Authorisation
This is the process of ensuring that the specific user has the rights required to perform the action requested
## Accountability
Accountability is the process of creating a record of the actions performed by users
# Cookies versus Tokens
## Cookie-Based session management
Once a web application wants to begin tracking, in a response, the Set-Cookie header value is sent which the browser will interpret to store a new cookie value. Your browser browser will then create a cookie entry for the set cookie with the value given, which will be valid for the domain where the cookie was received from, several attributes, here are noteworthy ones:
- Secure: these cookies may only be used over HTTPS, if there are certificate errors or HTTP is used the cookie will not be transmitted
- HTTPOnly: indicates to the browser that the cookie value may not be read by client-side javascript
- Expire: indicates to the browser when a cookie value will no longer be valid an should be removed
- SameSite: Indicates to the browser whether the cookie may be transmitted in cross-site requests to help protect against CSRF attacks
A key thing to remember that with cookie-based authentication is that the browser itself will decide when a certain cookie value will be sent with a request
## Token-Based session managment
Token-based session management uses client side code for the process, after authentication the web application provides a token within the request body, using client side java script code, this token is then stored in the browsers LocalStorage
When a new request is made, javascript code must load the token from storage and attach it as a header. One of the most common types of tokens is JSON Web Tokens (JWT), which are passed through the `Authorization: Bearer` header
## Benefits and drawbacks

| **Cookie-Session Management**                                                                                                                        | **Token-Based Session Management**                                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Cookie is automatically sent by the browser with each request                                                                                        | Token has to be submitted as a header with each request using client-side JavaScript                                                                                     |
| Cookie attributes can be used to enhance the browser's protection of the cookie                                                                      | Tokens do not have automatic security protections enforced and should, therefore, be safeguarded against disclosures                                                     |
| Cookies can be vulnerable to conventional client-side attacks such as CSRF, where the browser is tricked into making a request on behalf of the user | As the token is not automatically added to any request and cannot be read from LocalStorage by other domains, conventional client-side attacks such as CSRF are blocked  |
| As cookies are locked to a specific domain, it can be difficult to use them securely in decentralised web applications                               | Tokens work well in decentralised web applications, as they are managed through JavaScript and can often contain all the information required to verify the token itself |

