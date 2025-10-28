# whois
whois is a request and response protocol that follows the RFC 3912 specification. A whois server listens on TCP port 43 for incoming requests. The domain registrar is responsible for maintaining the whois records for the domain names it is leasing
## What can you find
- Registrar: via which registrar was the domain name registered
- Contact info of registrant: name, organisation, address, phone, etc
- Creation, update, and expiration dates: when the domain name was first registered, last updated, and when it needs to be renewed
- Name server: which server to ask to resolve the domain name
# nslookup or dig
nslookup which stands for name server look up is used to find the IP address of a domain name, using various options you can get different results from the name server
for more advanced DNS queries and additional functionality you can use dig which stands for domain information groper

| Query type | Result             |
| ---------- | ------------------ |
| A          | IPv4 address       |
| AAAA       | IPv6 address       |
| CNAME      | Canonical name     |
| MX         | Mail Servers       |
| SOA        | Start of Authority |
| TXT        | TXT Records        |
# DNSDumpster
https://dnsdumpster.com/
DNSDumpster is a domain research tool that can discover hosts related to a domain
# Shodan
https://www.shodan.io/
shodan.io tries to connect to every device reachable online to build a search engine of connected "things" in contrast with a search engine for web pages