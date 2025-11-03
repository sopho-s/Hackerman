# Windows privileges
privileges are rights that an account has to perform specific system-related tasks, each user has a set of assigned privileges that can be checked with the following command
```shell-session
whoami /priv
```
a list of exploitable privileges are [here](https://github.com/gtworek/Priv2Admin)
# SeBackup/SeRestore
SeBackup and SeRestore privileges allow users to read and write to any file in the system, ignoring any Discretionary Access Control List (DACL) in place. The idea behind this this privilege is to allow certain users to perform backups from a system without requiring full administrative privileges
to backup the SAM and SYSTEM hashes you can use the following commands
```shell-session
reg save hklm\system <backuplocation>
```
```shell-session
reg save hklm\sam <backuplocation>
```
# SeTakeOwnership
SeTakeOwnership privilege allows a user to take ownership of any object on the system, including files and registry keys
for this we will abuse utilman.exe
Since Utilman is run with SYSTEM privileges, we will effectively gain SYSTEM privileges if we replace the original binary for any payload we like, to take ownership we will use the following command
```shell-session
takeown /f C:\Windows\System32\Utilman.exe
```
This does not immediately give us full privileges over it, but we can do that using icacls
```shell-session
icacls C:\Windows\System32\Utilman.exe /grant <user>:F
```
then replace it with a command prompts
```shell-session
copy cmd.exe utilman.exe
```
# SeImpersonate/SeAssignPrimaryToken
These privileges allow a process to impersonate other users and act on their behalf. Impersonation usually consists of being able to spawn a process or thread under the security context of another
this exploit uses the RogueWinRM exploit, this works because whenever a user starts the BITS service in Windows, it automatically creats a connection to port 5985 using SYSTEM privileges normally used for WinRM which is simply a port that exposes a powershell console to be used remotely through the network. if for some reason the WinRM service isn't running on the victim server, an attacker can start a fake WinRM service on port 5985 and catch the authentication attempt made by the BITS service when starting. If the attacker has SeImpersonate privileges, he can execute any command on behalf of the connecting user, which is SYSTEM
