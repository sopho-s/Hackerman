Simple mail transfer protocol is one of the most used services on the internet, it is used to communicate with an MTA server, an MTA server is used to store and transfer emails from senders to recipients. SMTP uses cleartext where all commands are sent without encryption
# Details
- default port is 25
- uses tcp
# Enumeration
## MSF auxiliary/scanner/smtp/smtp_version
gets the version of smtp running
## MSF auxiliary/scanner/smtp/smtp_enum
enumerates users on the smtp server