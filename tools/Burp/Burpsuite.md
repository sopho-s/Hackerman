# Tools
## Proxy
Proxy enables interception and modification of requests and responses while interacting with web applications
## Repeater
Repeater allows for capturing, modifying, and resending the same request multiple times. This functionality is particularly useful when crafting payloads through trial and error
## Intruder
Intruder allows for spraying endpoints with requests, commonly used for brute-force attacks or fuzzing endpoints
## Decoder
Decoder offers a valuable service for data transformation. It can decode captured information or encode payloads before sending them to the target
## Comparer
Comparer enables the comparison of two pieces of data at the word or byte level
## Sequencer
Sequencer is typically employed when assessing the randomness of tokens, such as session cookie values or other supposedly randomly generated data
## Target
target allows you to have more control over the scope of testing
### Site map
This sub-tab allows you to map out the web applications we are targeting in a tree structure, every page that is visited while proxy is active will be displayed on the site map
### Issue definitions
Issue definitions allows you to see an extensive list of web vulnerabilities, complete with descriptions and references
### Scope settings
this allows you to control the target scope in burpsuite which allows you to include or exclude specific domains/IPs to define the scope of testing
# Options
## Global settings
These settings affect the entire Burp Suite installation and are applied every time you start the application
## Project settings
These settings are specific to the current project and apply only during the session