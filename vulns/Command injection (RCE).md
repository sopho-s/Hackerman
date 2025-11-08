Command injection is the abuse of an application's behaviour to execute commands on the operating system, using the same privileges that the application on a device is running with
# Remediations
## Input sanitisation
sanitising any input from a user that an application uses is a great way to prevent command injection

using hex can get around this tho
# cool workarounds
```shell
printf "\x00"
```
this actually will evaluate hex to normal ASCII, use this as you will
```shell
ech$@o hello
```
will run `echo hello`
```shell
echo <<< echo hello
```
<<< will redirect the right hand side equation to stdin of the left