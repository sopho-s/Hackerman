WinRM is a remote access protocol that works over HTTP or HTTPS. It is typically used to:
- Remotely access and interact with windows hosts on a local network
- Remotely access and execute commands on Windows systems
- Manage and configure Windows systems remotely
# Details
- default port is 5985/5986
- uses tcp
# crackmapexec
https://github.com/byt3bl33d3r/CrackMapExec
```shell
crackmapexec winrm ip -u username -p wordlist
```
# evil-winrm.rb
https://github.com/Hackplayers/evil-winrm
```shell
evil-winrm.rb -u username -p 'password' -i ip
```