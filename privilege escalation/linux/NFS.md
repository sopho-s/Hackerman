Privilege escalation vectors are not confined to internal access. Shared folders and remote management interfaces such as SSH and Telnet can help you gain root access on the target system
NFS configuration is kept in the /etc/exports file. This file is created during the server installation and can usually be read by users
NFS by default will change the root user to nfsnobody and strip away any file from the operating system with root privs. if the "no_root_squash" option is present on the writable share, we can create an executable with SUID bit set and run it on the target system
you can find mountable shares from the attacking machine with
```shell
showmount -e ip
```
```shell
mount -o rw i:directorytomount mountdirectory
```