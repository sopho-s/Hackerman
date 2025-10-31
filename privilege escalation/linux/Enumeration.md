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
# env
the env command will show environmental variables
# sudo -l
the target system may be configured to allow users to run some commands with root privileges. The sudo -l command can be used to list all commands your user can run using sudo
# id
id can give a general overview of the user's privilege level and group memberships
# /etc/passwd
reading /etc/passwd can be an easy way to discover users on the system
# history
history can list previous commands and, albeit rarely, have stored information such as passwords and usernames
# ifconfig
can show network interfaces that are on the computer
# ip route
can show which network routes exist
# netstat
netstat -a shows all listening ports and established connections
netstat - at or netstat -au shows TCP or UDP protocols respectively
netstat -l lists ports in listening mode
netstat -s lists network usage stats by protocol
netstat -tp lists connections with the service name and PID info
netstat -i shows interface statistics
-n does not resolve names
-o displays timers
# find
can be used to find certain files on the system
- `find . -name flag1.txt`: find the file named “flag1.txt” in the current directory
- `find /home -name flag1.txt`: find the file names “flag1.txt” in the /home directory
- `find / -type d -name config`: find the directory named config under “/”
- `find / -type f -perm 0777`: find files with the 777 permissions (files readable, writable, and executable by all users)
- `find / -perm a=x`: find executable files
- `find /home -user frank`: find all files for user “frank” under “/home”
- `find / -mtime 10`: find files that were modified in the last 10 days
- `find / -atime 10`: find files that were accessed in the last 10 day
- `find / -cmin -60`: find files changed within the last hour (60 minutes)
- `find / -amin -60`: find files accesses within the last hour (60 minutes)
- `find / -size 50M`: find files with a 50 MB size
# Linux auto enum tools
- **LinPeas**: [https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS)
- **LinEnum:** [https://github.com/rebootuser/LinEnum](https://github.com/rebootuser/LinEnum)[](https://github.com/rebootuser/LinEnum)
- **LES (Linux Exploit Suggester):** [https://github.com/mzet-/linux-exploit-suggester](https://github.com/mzet-/linux-exploit-suggester)
- **Linux Smart Enumeration:** [https://github.com/diego-treitos/linux-smart-enumeration](https://github.com/diego-treitos/linux-smart-enumeration)
- **Linux Priv Checker:** [https://github.com/linted/linuxprivchecker](https://github.com/linted/linuxprivchecker)