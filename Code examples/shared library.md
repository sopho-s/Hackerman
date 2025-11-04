example program to use for loading shared library
```c
#include <stdio.h>
#include <stdlib.h>
int main() {
	char command[100];
	scanf("%s", command);
	system(command);
}
```
```shell-session
gcc -shared -fPIC elevate.c -o elevate.so
```