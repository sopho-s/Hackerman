# hostname
the hostname command returns the hostname of the target machine, although this value can be easily changed or have a meaningless value, in somecases it will provide info about the system's role within a corporate network
# uname - a
this will print the system information and give additional details about the kernel used by the system. this will be useful when searching for any potential kernel vulnerabilities that could lead to privilege escalation
# /proc/version
the proc filesystem provides information about the target system processes. You will find proc on many different linux flavours. This may give you information on the kernel version and additionaly data such as whether a compiler is installed
# /etc/issue
Systems can also be identified by looking at the /etc/issue file. This file usually contains some information about the operating system but can easily be changed
# ps
the ps command is an effective way to see the currently running processes on a linux system. Typing ps on your terminal will show processes for the current shell
## Useful options
ps -A will show all running processes
ps axjf will show the process tree
ps aux will show the processes for all users, display the user that launched the process and show the processes that are not attached to the terminal