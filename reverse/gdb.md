gdb is a binary debugger that allows you to debug the assembly operations of the code
# gef
gef is an extension to gdb that adds additional functionality to the debugger which will help you debug better
# common commands
## break (b)
sets a breakpoint at the given location
you can use \*main+25 to set a breakpoint at main+25 address
or you could mention a specific address like \*0x8048414
## run (r)
runs the program
## next
takes you through one line of code, but will step over function calls
## step
takes you through one line of code, but will step into functions
## stepi
takes you through one instruction, stepping into function calls
## nexti
goes to the next instruction
## disassemble (disass)
disassembles the given function
## info
gives you information about a specific detail
### breakpoints
gives you information about breakpoints
### frame
gives you information about the stack fram
### registers
gives you all of the registers
## delete (del)
deletes a breakpoint
## x
can be used to examine things, using / you can specify what you want to examine
- x/a shows the address of the specified 
- x/nc will show you n characters
- x/s shows you the string
- x/g shows you the qword
- x/w shows you the dword
## set
you can use set to set certain values while running code
`set {<type> [<size>]} <mem-location> = <value>`
`set <dereferenced-mem-location> = value`
# jmp (j)
jumps to a specific memory location
