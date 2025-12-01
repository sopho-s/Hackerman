SSRF stands for server-side request forgery, its a vulnerability that allows malicious users to cause the webserver to make an additional or edited HTTP request to the resource of the attackers choosing
# Where to find
Potential ssrf vulns can be spotted in web applications in many different ways, for example a full url is used in the address bar, if a url is in a hidden field form, partial urls such as just the hostname, or sometimes just the path of the url
# Why is this so coolioso
Resources you cant access but the server can, can now be accessed through the server, this means sensitive data can be accessed, DoS, or even further scanning of internal networks
# Getting past DEFENCES
## Deny list
a deny list is where all requests are accepted apart from resources specified in a list or matching a particular pattern. Using alternative local host references or subdomains can bypass local host attacks
ips such as 169.254.169.254 could contain important meta data about the deployed cloud server
## Allow list
allow list is where all request get denied unless they appear on a list or match a particular pattern, if the rule is like that a url parameter must begin with a certain url an attacker can register a url with the server url as a subdomain
## Open Redirect
An Open Redirect Vulnerability entails an attacker manipulating the user and redirecting them from one site to another site
# How to prevent
- Implement strict input validation and sanitise all user-provided input
- Instead of a block list, maintain an allow list instead
- Implement network segmentation to isolate sensitive internal resources
- Implement security headers, such as content-security-policy, that restricts the application's load of external resources
- Implement strong access controls for internal resources
- Implement comprehensive logging nad monitoring