in some scenarios, web applications are written to request access to files on a given system including images, static text, and so on via parameters
# Path traversal
also known as a directory traversal, a web security vulnerability allows an attacker to read operation system resources, such as local files on the server running an application
# Local file inclusion
LFI occurs when a web application allows users to include files from the local file system allowing you to retrieve sensitive files and have it included on the webpage
# Remote file inclusion
This occurs when the web application allows the attacker to inject an external url into the include function
# PHP session files
PHP session files can also be used in a LFI attack, leading to RCE, anything stored in the session can be accessed from /var/lib/php/sessions/sess_\[sessionID], this can be used to see how the session is structured, or maybe you could plant code into the session and read it from their
# Log poisoning
Log poisoning is a technique where an attacker injects executable code into a web server's log file and then uses an LFI vulnerability to include and execute this log file
# Wrapper RCE
filters can also be used to directly execute code (ooo spooky) here is a cool lil payload for you to consider `php://filter/convert.base64-decode/resource=data://plain/text,PD9waHAgc3lzdGVtKCRfR0VUWydjbWQnXSk7ZWNobyAnU2hlbGwgZG9uZSAhJzsgPz4+&cmd=`
# some errors
sometimes the include will append an extension at the end, using a null byte %00 can get around this as they may think the end of the string is where the %00 byte is

sometimes when using $\_REQUESTS using a post request instead of a get and using url encoded parameters may change the results of what gets shown

some websites will attempt to stop traversal by making it so only files within a certain directory can be used, using filter bypasses while still including the base directory can usually bypass bad ones
# Remediations
- Keep system and services updated
- Turn off PHP errors to avoid leaking the path of the application and other potentially revealing information
- WAF mitigates web application attacks
- Disable php features that cause file inclusion vulns if your web app does not need them such as allow_url_fopen or allow_url_include
- Carefully analyse the web application and allow only protocols and php wrappers that are in need
- never trust user input and enable proper input validation
- Implement whitelisting for filenames as well as black listing
# Thingies to do
- Find the flipin application running
- look through all processes using `/proc/[pid]/cmdline`
- `php://filter/convert.base64-encode/resource` pretty sickalishos way of displaying php files
- if you can do php filters then heor https://github.com/synacktiv/php_filter_chain_generator https://www.synacktiv.com/publications/php-filters-chain-what-is-it-and-how-to-use-it
- apache logs, if they record user agents, may be able to do custom agent with php name and execute it 
- ini files can usually contain information about database locations
- /etc/apache2/sites-available/000-default.conf
- `data:text/plain,<?php%20phpinfo();%20?>` is a nice payload to try