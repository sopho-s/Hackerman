in some scenarios, web applications are written to request access to files on a given system including images, static text, and so on via parameters
# Path traversal
also known as a directory traversal, a web security vulnerability allows an attacker to read operation system resources, such as local files on the server running an application
# Local file inclusion
LFI occurs when a web application allows users to include files from the local file system allowing you to retrieve sensitive files and have it included on the webpage
# Remote file inclusion
This occurs when the web application allows the attacker to inject an external url into the include function
# some errors
sometimes the include will append an extension at the end, using a null byte %00 can get around this as they may think the end of the string is where the %00 byte is

sometimes when using $\_REQUESTS using a post request instead of a get and using url encoded parameters may change the results of what gets shown
# Remedations
- Keep system and services updated
- Turn off PHP errors to avoid leaking the path of the application and other potentially revealing information
- WAF mitigates web application attacks
- Disable php features that cause file inclusion vulns if your web app does not need them such as allow_url_fopen or allow_url_include
- Carefully analyse the web application and allow only protocols and php wrappers that are in need
- never trust user input and enable proper input validation
- Implement whitelisting for filenames as well as black listing