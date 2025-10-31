SUID and SGID bit allows you to execute the permission of the owner or group respectively
to find these file you can use the following command
```shell
find / -type f -perm -04000 -ls 2>/dev/null
```
