Race conditions occur when the timing of events of a program influence the behavior and outcome of the program
# TOCTOU
A Time-of-Check to Time-of-Use vulnerability is when two threads read a variable as the same value before one of them updates them
# Remediations
- Synchronising mechanisms like locks can prevent accessing shared resources at the same time
- Atomic operations make sure that a set of instructions grouped together can finish without being interrupted
- Data base transactions group multiple operations into one unit, consequently all operations within the transaction either succeed as a group or fail as a group