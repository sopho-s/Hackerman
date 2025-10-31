# Unattended windows installations
When installing windows on a large number of hosts, administrators may use Windows Deployment Services, which allows a single operating system image to be deployed to several hosts through the network. Such installations use an administrator account to perform the initial setup which might end up being stored in the machine in the following locations
- C:\Unattend.xml
- C:\Windows\Panther\Unattend.xml
- C:\Windows\Panther\Unattend\Unattend.xml
- C:\Windows\system32\sysprep.inf
- C:\Windows\system32\sysprep\sysprep.xml
# Powershell history
whenever a user runs a command using powershell, it gets stored into a file that keeps a memory of past commands, this can be accessed with the following
```shell-session
type %userprofile%\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt
```
**Note:** The command above will only work from cmd.exe, as Powershell won't recognize `%userprofile%` as an environment variable. To read the file from Powershell, you'd have to replace `%userprofile%` with `$Env:userprofile`
# Saved windows credentials
Windows allows us to use other users' credentials. This function also gives the option to save these credentials on the system
```shell-session
cmdkey /list
```
you can apply useful ones with 
```shell-session
runas /savecred /user:<user> cmd.exe
```
# IIS configurations
Internet Information Services (IIS) is a default web server on Windows installations. The config file can usually be found in:
- C:\inetpub\wwwroot\web.config
- C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config
a quick way to find database connection string on the file is with this
```shell-session
type <config-file> | findstr connectionString
```
# Retrieving credentials from software: PuTTY
PuTTY is an ssh client commonly found on windows systems. Instead of having to specify a connection's parameters every single time, users can store sessions where the IP, user and other configs can be stored for later use. While it wont allow users to store their ssh password, it will store proxy configurations that include cleartext authentication credentials
to get the proxy creds you can use
```shell-session
reg query HKEY_CURRENT_USER\Software\SimonTatham\PuTTY\Sessions\ /f "Proxy" /s
```
