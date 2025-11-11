pwntool is a python ctf library used for rapid exploit development. it essentially helps us write exploits quickly
# basics
## importing it
```python
from pwn import *
```
## connecting to a remote server
```Python
target = remote("github.com", 9000)
```
## running target binary
```python
target = process("./challenge")
```
## attaching to gdb
```python
gdb.attach(target)
```
## attaching and immediately passing a command
```python
gdb.attach(target, gdbscript="b *main")
```
## sending a variable to the target
```python
target.send(x)
```
## receiving a single line from the target
```python
print(target.recvline())
```
## receiving until a specific string
```python
print(target.recvuntil("out"))
```
## pack an integer as a least endian qword and dword
```python
p64(x)
p32(x)
```
## unpack a least endian qword and dword as an integer
```python
u64(x)
u32(x)
```
## directly interact with target
```python
target.interactive()
```