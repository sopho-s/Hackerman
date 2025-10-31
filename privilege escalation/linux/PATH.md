If a folder which your user has write permission is located in the path, you could potentially hijack an application to run a script
writable folders can be found at 
```shell
find / -writable 2>/dev/null | cut -d "/" -f 2,3 | grep -v proc | sort -u
```
using
```shell
export PATH=/tmp:$PATH
```
you can add /tmp to the path variable which is most likely writable
