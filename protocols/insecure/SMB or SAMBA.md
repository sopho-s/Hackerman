SMB is a network file sharing protocol that is used to facilitate the sharing of files and peripherals between computer on a local network, SAMBA is the linux equivalent 
# Details
- default port is 445
- uses tcp
# Enumeration
## MSF auxiliary/scanner/smb/smb_version
finds the smb version running
## MSF auxiliary/scanner/smb/smb_enumusers
finds all users on the smb program
## MSF auxiliary/scanner/smb/smb_enumshares
gets all shares on the smb progra
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