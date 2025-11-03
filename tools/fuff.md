# args
## -w
selects which wordlist to use
## -u
Selects which url to use
## -X
specifies the request type
## -d
parameters
## -fc
specifies the filter code
## -fs
specifies the filter http response size
## -t
Specifies the amount of threads that run on ffuf
## -s
specifies to run on silent mode
## -sa
stop on all error cases
## -H
specifies headers

# example
```shell
ffuf -w /usr/share/wordlists/SecLists/Usernames/xato-net-10-million-usernames.txt -u http://lookup.thm/login.php -X POST -d "username=FUZZ&password=password123" -fw 10 -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" -t 20
```