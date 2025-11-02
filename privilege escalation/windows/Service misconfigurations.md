Window services are managed by the Service Control Manager. The SCM is a process in charge of managing the state of services as needed
Each service on a windows machine will have an associated executable which will be run by the SCM whenever a service is started. It is important to note that service executables implement special functions to be able to communicate with the SCM, and therefore not any executable can be started as a service successfully. Each service also specifies the user account under which the service will run
to query a specific service you can use the following
```shell-session
sc qc <service>
```
Services have a Discretionary Access Control List (DACL), which indicates who has permission to start, stop, pause, query status, query configuration, or reconfigure the service, amongst other privileges. the DACL can be seen from Process Hacker
All service configurations are stored on the registry under `HKLM\SYSTEM\CurrentControlSet\Services\
# Insecure permissions on service executables
If an executable associated with a service has weak permissions that allow an attacker to modify or replace it, the attacker can gain the privileges of the service's account trivially
to check the permissions on the binary you can use
```shell-session
icacls <binary>
```
# Unquoted service paths
When working with Windows services, a very particular behaviour occurs when the service is configured to point to an "unquoted" executable, if there are spaces in the binary path name it could be interpreted multiple ways
for example with
```shell-session
C:\MyPrograms\Disk Sorter Enterprise\bin\disksrs.exe
```
it could be interpreted as

| Command                                              | Argument 1                 | Argument 2                 |
| ---------------------------------------------------- | -------------------------- | -------------------------- |
| C:\MyPrograms\Disk.exe                               | Sorter                     | Enterprise\bin\disksrs.exe |
| C:\MyPrograms\Disk Sorter.exe                        | Enterprise\bin\disksrs.exe |                            |
| C:\MyPrograms\Disk Sorter Enterprise\bin\disksrs.exe |                            |                            |
while it should fail, it doesn't because SCM tries to help the user and starts searching for it in the order of the table
# Insecure service permissions
Should the service DACL allow you to modify the configuration of a service, you will be able to reconfigure the service.
to check for a service DACL from the command line, you can use accesschk from the Sysinternals suite
```shell-session
accesschk64.exe -qlc <service>
```
when changing what a service runs at you can use the following command to do as such
```shell-session
sc config <service> binPath= "<binary>" obj= LocalSystem
```
