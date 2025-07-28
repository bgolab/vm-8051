# vm-8051
stack-based vm for 8051
---
I recently discovered modern 8051 MCU versions in many popular DIY kits, and decided to implement a kind of toy vm. 
To simplify things and be able to fit the binary in constraind evironment the stack-based architecture was selected.
Stack-based architectures assumes RPN-like ISA design (we put data on data stack, call function which will consume the data and will return the resulst alaso on the stack).

Current assumptions:
-UART is used to enter commnads, both OS-like and VM language mnemonics,
-the commands will be parsed immediatelly, the OS-like commands will be executed, the VM commands will be tokenized & compiled to binary form

OS-like commands:
- x (eXecute) - starts VM and runs programs
- s (show state) - reveals internal VM state (bytecode, data & return stacks, registers, etc)

