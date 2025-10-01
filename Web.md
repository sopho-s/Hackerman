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