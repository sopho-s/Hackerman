Hypertext transfer protocol is the protocol used to transfer web pages. Your web browser connects to the webserver and uses HTTP to request HTML pages and images among other files and submit forms and upload various files
# How it works
HTTP sends and recieves data as cleartext, you can send requests to the server, which the server will then respond appropriately with the requested data, or not if there is an error
# Details
- default port is 80
- uses tcp
# Enumeration
## MSF auxiliary/scanner/http/http_version
shows the version of the webserver
## MSF auxiliary/scanner/http/http_header
shows the headers of the http request to a certain page
## MSF auxiliary/scanner/http/robots_txt
finds the robots.txt file (idk why you need this)
## MSF auxiliary/scanner/http/http_login
brute forces login for http authentication
## MSF auxiliary/scanner/http/apache_userdir_enum
apache with the useerdir directive enabled generates different error codes when a username exists, naughty naughty