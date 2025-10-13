# args
## -t
sets the amount of threads to scan
## -w
sets the wordlist
## --delay
sets the delay between sending requests
## --debug
helps troubleshoot when command gives errors
## -o
writes the enumeration results to a file we choose
# dir
enumerates directories from a given url
## example
```shell
gobuster dir -u "<url>" -w <wordlist> -t <threadcount>
```

## -c
configures the cookies
## -x
sets the file extensions
## -H
configures the header to pass along with each request
## -k
this skips the certificate check
## -n
stops the display of status codes
## -P
sets the password
## -s
sets which status codes you wish to see
## -b
sets the status codes you dont wish to see
## -U
sets the username
## -r
follows the redirect
## -u
sets the target url
# dns
enumerates subdomains of a given domain
## example
```shell
`gobuster dns -d <domain> -w <wordlist>
```
## -c
shows the cname records
## -i
shows the ip of the domain
## -r
configures a custom dns server to use for resolving
## -d
configures the domain you want to enumerate
# vhost
finds other hosts that a server is using
## example
```shell
gobuster vhost -u <url> -w <wordlist>
```
## -u
specifies the base url
## -m
specifies the http method used for requests
## -r
follows a http redirect
## --exclude-length
excludes results based on the length of the response body to filter out unwanted responses
## --append-domain
adds the domain to the end of the subdomain