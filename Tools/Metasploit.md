# Metasploit db
Metasploit has a database function to simplify project management and avoid possible confusion when setting up parameter values
```bash
systemctl start postgresql
sudo -u postgres msfdb init
```
using `db_nmap` now stores all results in the database
using `hosts` and `services` can show all about the hosts and services found
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
- `set [parameter-name] [value]`
sets the parameters in a module to a certain value
## setg
- `setg [parameter-name] [value]`
sets the parameter globally to a certain value
## unset
- `unset [parameter-name]`
clears any parameter or can be used with `all` to clear all parameters
## unsetg
- `unsetg [parameter-name]`
clears any parameter globably
## exploit
- `exploit`
runs the module
## check
- `check`
checks if the target system is vulnerable without exploiting it
## background
- `background`
pushes the run exploit to the background and brings you back to the msfconsole
## sessions
- `sessions`
shows all existing sessions
`sessions -i [session-number]` allows you to interact with the session 
## workspace
- `workspace`
lists all workspaces
`workspace -a/-d` adds and deletes a workspace respectively
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
# Parameters
- RHOSTS: "Remote host" the IP address of the target system. A single IP address or a network range can be set. It also supports CIDR notation
- RPORT: "Remote port" the port on the target system the vulnerable application is running on
- PAYLOAD: the payload you will use with the exploit
- LHOST: "Localhost" the attacking machine's IP address
- LPORT: "Local port" the port you will use for the reverse shell to connect back to
- SESSION: each connection established to the target system using Metasploit will have a session ID
# Msfvenom
msfvenom allows you to access all payloads available in the metasploit framework
## args
### -p
specifies which payload you want
### LHOST
specifies the machine you want to connect from
### -e
specifies which encoding method you want
### -f
specifies which format you want the payload in
### -l
lists about a certain option
## listenting
when using a meterpreter reverse shell, one can use the module `exploit/multi/handler` to connect
# Meterpreter migration
This is how migrate works in meterpreter:  

1. Get the PID the user wants to migrate into. This is the target process.
2. Check the architecture of the target process whether it is 32 bit or 64 bit. It is important for memory alignment.
3. Check if the meterpreter process has the SeDebugPrivilege. This is used to get a handle to the target process. Further details at [http://support.microsoft.com/kb/131065](http://support.microsoft.com/kb/131065)
4. Get the actual payload from the handler that is going to be injected into the target process. Calculate its length as well.
5. Call the OpenProcess() API to gain access to the virtual memory of the target process.
6. Call the VirtualAllocEx() API to allocate an RWX (Read, Write, Execute) memory in the target process
7. Call the WriteProcessMemory() API to write the payload in the target memory virtual memory space.
8. Call the CreateRemoteThread() API to execute the newly created memory stub having the injected payload in a new thread.
9. Shutdown the previous thread having the initial meterpreter running in the old process.
# Useful meterpreter extensions
## kiwi
has a bunch of useful cred retrieval