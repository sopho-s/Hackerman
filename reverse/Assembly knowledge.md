# parameter passing and returns
## x64
1. rdi
2. rda
3. rcx
4. r8
5. r9
6. stack etc

values are returned from the rax register
## x86
all arguments are passed on the stack
values are returned from the eax register
# Instructions
## mov
the move instruction just moves data from one register to another
```assembly
mov rax, rdx
```
this will move data from rdx to rax
## dereference
\[\] are used to dereference pointers
```assembly
mov rax, [rdx]
```
## lea
the lea instruction calculates the address of the second operand and moves that address in the first
```assembly
lea rdi, [rbx+0x10]
```
moves the address rbx+0x10 into the rdi register
## add
this adds two values together and stores the sum in the first argument
```assembly
add rax, rdx
```
## sub
this subtracts the second operand from the first one and stores the result in the first argument
```assembly
sub rsp, 0x10
```
## xor
this will perform an xor operation on the two arguments as it is given an store the result in the first operand
```assembly
xor rdx, rax
```
## push
this will grow the stack by 8 bytes for x64 or 4 bytes for x86 and then push the contents of a register onto the new stack space
```assembly
push rax
```
## pop
the pop instruction will pop the top 8 bytes for x64 or 4 bytes for x86 off the stack and into the argument then shrink the stack by the same amount
```assembly
pop rax
```
## jmp
the jump instruction will jump to an instruction address and is used to redirect code execution
```assembly
jmp 0x602010
```
## call & ret
similar to the jump instruction. the difference is that it will push the values of rbp and rip onto the stack then jump to whatever address is given, after the ret is called it pops the rbp and rip off the stack and continues execution
## cmp
cmp is similar to the sub instruction except it does not store the result, it checks if the result is less than zero, greater than zero, or equal to zero. Depending on the value it will set the flags accordingly
## jnz/ jz
the jump if not zero and jump if zero are similar to the jump instruction except they only execute depending on the status of the zero flag