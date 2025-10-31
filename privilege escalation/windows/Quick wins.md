# Scheduled tasks
Scheduled tasks may have lost its binary or have a binary you can modify, this may allow you to escalate you privilages
you can list scheduled tasks with
```shell-session
schtasks
```
and get a more detailed view
```shell-session
schtasks /query /tn <task> /fo list /v
```
to check if you can overwrite something that a task is using you can use icacls to find out who can edit it
# AlwaysInstallElevated
Windows installer files normally run with the privilege of the user that starts it, though this can be configured to run at higher privilege levels from any user account
this method requires two registry values to be set. you can query these from the command line using the commands below
```shell-session
reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer
reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer
```
you can then execute msi with the following
```shell-session
msiexec /quiet /qn /i C:\Windows\Temp\malicious.msi
```
