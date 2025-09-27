# Commands
## use
- `use [module]`
lets you use the module specified
can also use the numbers at the beginning of the search result line
## show
- `show [options]`
### options
- `show options`
can be used when you have selected a module to view the options you can set for the module
### payloads
- `show payloads`
shows compatible payloads for the module selected
## back
exits the current context
## info
gives further info that can be obtained about the current module
## search
- `search [search-term]`
this will search the mf database for modules relevant to the given search parameters
- `search type:[type] [search-term]`
this can be used to specify the type of module one is searching for
## set 
# Types of modules
## Auxiliary
Any supporting module, such as scanners, crawlers and fuzzers
## Encoders
Encoders will allow you to encode the exploit and payload in the hope that a signature-based antivirus solution may miss them
## Evasion
While encoders will encode the payload, they should not be considered a direct attempt to evade antivirus software. On the other hand, "evasion" modules will try that, with more or less success
## Exploits
self explanatory lol
## NOPs
NOPs do nothing, they are often used as a buffer to achieve consistent payload sizes
## Payloads
Payloads are codes that will run on the target system. Exploits will leverage a vulnerability on the target system, but to achieve the desired result we need the payload
### Types of payloads
#### Adapters
An adapter wraps a single payload and converts them into different formats. For example, a normal single payload can be wrapped inside a powershell adapter, which will make a single powershell command that will execute the payload
#### Singles
Self-contained payloads that do not need to download an additional component to run
#### Stagers
Responsible for setting up a connection channel between Metasploit and the target system. Useful when working with staged payloads. "Staged payloads" will first upload a stager on the target system then download the rest of the payload (stage). This provides some advantages as the initial size of the payload will be relatively small compared to the full payload sent at once
#### Stages
Downloaded by the stager. this will allow you to use larger sized payloads
## Post
Post modules will be useful on the final stage of the penetration testing process listed above, post-exploitation