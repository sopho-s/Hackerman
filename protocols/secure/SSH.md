Secure shell was created to provide a secure way for remote system administration. It lets you securely connect to another system over the network and execute commands on the remote system
# Details
- default port is 22
- uses tcp
# Enumeration
## MSF auxiliary/scanner/ssh/ssh_version
gets the ssh version of the service
## MSF auxiliary/scanner/ssh/ssh_login
idk why just use hydra
## MSF auxilary/scanner/ssh/ssh_enumusers
finds users