# ENUMERATION
- [x] Service nmap scan
- [x] Script nmap scan if you have determined that it wont notify the user
- [x] Gobuster dir scan (make sure to add extensions)
- [ ] Gobuster dns scan
- [x] Get version numbers from wappalyzer 
- [ ] Search if versions are vulnerable to any cve
# Privilege escalation
- [x] Is /etc/passwd writable
- [x] Is /etc/shadow readable
- [x] Are there any plain text or encrypted passwords hidden in databases or in password files
- [x] Enumerate /opt
- [x] Can the user do anything with sudo
- [x] Are there any obvious suid bits that can be abused
- [x] Are there any capabilities that can be abused
- [x] Are there any obvious cron jobs
- [x] Are there any hidden cron jobs (pspy)
- [x] Are there any open ports (netstat -lntu)
- [ ] Run linpeas.sh