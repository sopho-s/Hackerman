# HTTP Message
follow this format
## Start Line
The start line is like the introduction of the message. It tells you what kind of message is being sent—whether it's a request from the user or a response from the server. This line also gives important details about how the message should be handled.
## Headers
Headers are made up of key-value pairs that provide extra information about the HTTP message. They give instructions to both the client and the server handling the request or response. These headers cover all sorts of things, like security, content types, and more, making sure everything goes smoothly in the communication.
## Empty Line
The empty line is a little divider that separates the header from the body. It’s essential because it shows where the headers stop and where the actual content of the message begins. Without this empty line, the message might get messed up, and the client or server could misinterpret it, causing errors.
## Body
The body is where the actual data is stored. In a request, the body might include data the user wants to send to the server (like form data). In a response, it’s where the server puts the content that the user requested (like a webpage or API data).
# HTTP Request
## Request Line

The **request line** (or start line) is the first part of an HTTP request and tells the server what kind of request it’s dealing with. It has three main parts: the **HTTP method**, the **URL path**, and the **HTTP version**.

**Example:** `METHOD /path HTTP/version`

## HTTP Methods

The **HTTP method** tells the server what action the user wants to perform on the resource identified by the URL path. Here are some of the most common methods and their possible security issue:

### GET  
**Used to fetch** data from the server without making any changes. Reminder! Make sure you’re only exposing data the user is allowed to see. Avoid putting sensitive info like tokens or passwords in GET requests since they can show up as plaintext.

### POST  
**Sends** data to the server, usually to create or update something. Reminder! Always validate and clean the input to avoid attacks like SQL injection or XSS.

### PUT  
**Replaces or updates** something on the server. Reminder! Make sure the user is authorised to make changes before accepting the request.

### DELETE  
**Removes** something from the server. Reminder! Just like with PUT, make sure only authorised users can delete resources.

Besides these common methods, there are a few others used in specific cases:

### PATCH  
**Updates part of a resource. It’s useful for making small changes without replacing the whole thing, but always validate the data to avoid inconsistencies.

### HEAD  
**Works like GET but only retrieves headers, not the full content. It’s handy for checking metadata without downloading the full response.

### OPTIONS  
**Tells you what methods are available for a specific resource, helping clients understand what they can do with the server.

### TRACE  
**Similar to OPTIONS, it shows which methods are allowed, often for debugging. Many servers disable it for security reasons.

### CONNECT  
**Used to create a secure connection, like for HTTPS. It’s not as common but is critical for encrypted communication.

Each of these methods has its own set of security rules. For example, PATCH requests should be validated to avoid inconsistencies, and OPTIONS and TRACE should be turned off if not needed to avoid possible security risks.

## URL Path

The **URL path** tells the server where to find the resource the user is asking for. For instance, in the URL `https://tryhackme.com/api/users/123`, the path `/api/users/123` identifies a specific user.

Attackers often try to manipulate the URL path to exploit vulnerabilities, so it’s crucial to:

- Validate the URL path to prevent unauthorised access
- Sanitise the path to avoid injection attacks
- Protect sensitive data by conducting privacy and risk assessments

Following these practices helps protect your web application from common attacks.

## HTTP Version

The **HTTP version** shows the protocol version used to communicate between the client and server. Here’s a quick rundown of the most common ones:

- **HTTP/0.9** (1991)The first version, only supported GET requests.

- **HTTP/1.0** (1996)Added headers and better support for different types of content, improving caching.

- **HTTP/1.1** (1997)Brought persistent connections, chunked transfer encoding, and better caching. It’s still widely used today.

- **HTTP/2** (2015)Introduced features like multiplexing, header compression, and prioritisation for faster performance.

- **HTTP/3** (2022)Built on HTTP/2, but uses a new protocol (QUIC) for quicker and more secure connections.
### HTTP/2 vs HTTP/3
Although HTTP/2 and HTTP/3 offer better speed and security, many systems still use **HTTP/1.1** because it’s well-supported and works with most existing setups. However, upgrading to HTTP/2 or HTTP/3 can provide significant performance and security improvements as more systems adopt them.
# Request headers
Request headers allow extra information to be conveyed to the web server about the request. some common headers are as follows

| **Request Header** | **Example**                                                                    | **Description**                                                                         |
| ------------------ | ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------- |
| Host               | Host: tryhackme.com                                                            | Specifies the name of the web server the request is for                                 |
| User-Agent         | User-Agent: Mozilla/5.0                                                        | Shares information about the web browser the request is coming from                     |
| Referer            | Referer: https://www.google.com/                                               | Indicates the URL from which the request came from                                      |
| Cookie             | Cookie: user_type=student; room=introtowebapplication; room_status=in_progress | Information the web server previously asked the web browser to store is held in cookies |
| Content-Type       | Content-Type: application/json                                                 | Describes what type or format of data is in the request                                 |
# Request body
In HTTP requests such as POST and PUT, where data is sent to the web server as opposed to requested from the web server, the data is located inside the HTTP Request Body. The formatting of the data can take many forms, but some common ones are URL Encoded, Form Data, JSON, or XML
## URL encoded
A format where data is structured in pairs of key and value where (`key=value`). Multiple pairs are separated by an (`&`) symbol, such as `key1=value1&key2=value2`. Special characters are percent-encoded
### Example
```http
POST /profile HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Content-Type: application/x-www-form-urlencoded
Content-Length: 33

name=Aleksandra&age=27&country=US
```
## Form data
Allows multiple data blocks to be sent where each block is separated by a boundary string. The boundary string is the defined header of the request itself. This type of formatting can be used to send binary data, such as when uploading files or images to a web server
### Example
```http
POST /upload HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW

----WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="username"

aleksandra
----WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="profile_pic"; filename="aleksandra.jpg"
Content-Type: image/jpeg

[Binary Data Here representing the image]
----WebKitFormBoundary7MA4YWxkTrZu0gW--
```
## JSON
In this format, the data can be sent using the JSON (JavaScript Object Notation) structure. Data is formatted in pairs of name : value. Multiple pairs are separated by commas, all contained within curly braces { }.
### Example
```http
POST /api/user HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Content-Type: application/json
Content-Length: 62

{
    "name": "Aleksandra",
    "age": 27,
    "country": "US"
}
```
## XML
In XML formatting, data is structured inside labels called tags, which have an opening and closing. These labels can be nested within each other. You can see in the example below the opening and closing of the tags to send details about a user called Aleksandra.
### Example
```http
POST /api/user HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Content-Type: application/xml
Content-Length: 124

<user>
    <name>Aleksandra</name>
    <age>27</age>
    <country>US</country>
</user>
```
# Status Line
The status line is the first line in every http response and contains 3 key peices of info
1. **HTTP Version**: This tells you which version of HTTP is being used.
2. **Status Code**: A three-digit number showing the outcome of your request.
3. **Reason Phrase**: A short message explaining the status code in human-readable terms.
# Status Codes
## Informational Responses (100-199)
These codes mean the server has received part of the request and is waiting for the rest. It’s a "keep going" signal
## Successful Responses (200-299)
These codes mean everything worked as expected. The server processed the request and sent back the requested data
## Redirection Messages (300-399)
These codes tell you that the resource you requested has moved to a different location, usually providing the new URL
## Client Error Responses (400-499) 
These codes indicate a problem with the request. Maybe the URL is wrong, or you’re missing some required info, like authentication
## Server Error Responses (500-599)
These codes mean the server encountered an error while trying to fulfill the request. These are usually server-side issues and not the client’s fault
# Response Headers
When a web server responds to an HTTP request, it includes **HTTP response headers**, which are basically key-value pairs. These headers provide important info about the response and tell the client (usually the browser) how to handle it
## Required response headers
### Date
Example: `Date: Fri, 23 Aug 2024 10:43:21 GMT`  
This header shows the exact date and time when the response was generated by the server
### Content-Type
Example: `Content-Type: text/html; charset=utf-8`  
It tells the client what kind of content it’s getting, like whether it’s HTML, JSON, or something else. It also includes the character set (like UTF-8) to help the browser display it properly
### Server
Example: `Server: nginx`  
This header shows what kind of server software is handling the request. It’s good for debugging, but it can also reveal server information that might be useful for attackers, so many people remove or obscure this one
## Common Response headers
### Set-Cookie
Example: `Set-Cookie: sessionId=38af1337es7a8`  
This one sends cookies from the server to the client, which the client then stores and sends back with future requests. To keep things secure, make sure cookies are set with the `HttpOnly` flag (so they can’t be accessed by JavaScript) and the `Secure` flag (so they’re only sent over HTTPS)
### Cache-Control
Example: `Cache-Control: max-age=600`  
This header tells the client how long it can cache the response before checking with the server again. It can also prevent sensitive info from being cached if needed (using `no-cache`)
### Location
Example: `Location: /index.html`  
This one’s used in redirection (3xx) responses. It tells the client where to go next if the resource has moved. If users can modify this header during requests, be careful to validate and sanitise it—otherwise, you could end up with open redirect vulnerabilities, where attackers can redirect users to harmful sites
# Security headers
## Content-Security Policy (CSP)
A CSP header is an additional security layer that can help mitigate against common attacks like Cross-Site Scripting (XSS). Malicious code could be hosted on a separate website or domain and injected into the vulnerable website. A CSP provides a way for administrators to say what domains or sources are considered safe and provides a layer of mitigation to such attacks

Within the header itself, you may see properties such as `default-src` or `script-src` defined and many more. Each of these give an option to an administrator to define at various levels of granularity, what domains are allowed for what type of content. The use of self is a special keyword that reflects the same domain on which the website is hosted
### default-src
which specifies the default policy of self, which means only the current website.  
### script-src
which specifics the policy for where scripts can be loaded from, which is self along with scripts hosted on `https://cdn.tryhackme.com`  
### style-src
which specifies the policy for where style CSS style sheets can be loaded from the current website (self)
### TLDR
just stops external websites/scripts/styles being loaded or only certain trusted ones
## Strict-Transport-Security (HSTS)
The HSTS header ensures that web browsers will always connect over HTTPS
### max-age
This is the expiry time in seconds for this setting 
### includeSubDomains
An optional setting that instructs the browser to also apply this setting to all subdomains
### preload  
This optional setting allows the website to be included in preload lists. Browsers can use preload lists to enforce HSTS before even having their first visit to a website
## X-Content-Type-Options
The X-Content-Type-Options header can be used to instruct browsers not to guess the MIME time of a resource but only use the Content-Type header. This is good because a malicious actor could upload a jpg file that actually contains malicious js and when an unsuspecting user loads it, the MIME sniffer will detect it a js and run it as such instead of treating it as an image
### nosniff 
This directive instructs the browser not to sniff or guess the MIME type
## Referrer-Policy
This header controls the amount of information sent to the destination web server when a user is redirected from the source web server, such as when they click a hyperlink. The header is available to allow a web administrator to control what information is shared
### no-referrer
This completely disables any information being sent about the referrer        
### same-origin  
This policy will only send referrer information when the destination is part of the same origin. This is helpful when you want referrer information passed when hyperlinks are within the same website but not outside to external websites
### strict-origin
This policy only sends the referrer as the origin when the protocol stays the same. So, a referrer is sent when an HTTPS connection goes to another HTTPS connection
### strict-origin-when-cross-origin
his is similar to strict-origin except for same-origin requests, where it sends the full URL path in the origin header