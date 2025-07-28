# vm-8051
stack-based vm for 8051
---
I recently discovered modern STC 8051 MCU versions in many popular DIY kits, and decided to implement a kind of toy vm. 
To simplify things and be able to fit the binary in constraind evironment the stack-based architecture was selected.
Stack-based architectures assumes RPN-like ISA design (we put data on data stack, call function which will consume the data and will return the resulst alaso on the stack).

What is modern 8051: apart from having hw feature non-existent in the 80-ties like I2C, SPI it also uses flash memory, and has built-in flash programmer using UART to transfer and spark flashing process.

Current assumptions:
- UART is used to enter commnads, both OS-like and VM language mnemonics,
- the commands will be parsed immediatelly, the OS-like commands will be executed, the VM commands will be tokenized & compiled to binary form
- STC8G1K08A and STC15W50AS chips will be used but I assume very generic ISA, and capabilities
- Keil C51 will be used for the development

OS-like commands:
- x (eXecute) - starts VM and runs programs
- s (show state) - good for debugging to reveal internal VM state (bytecode, data & return stacks, registers, etc)
- t (trace) - good for debugging to trace proxes of execution
- r (reset state) - to clear vm state
- z (zeroize) - apart from resetting the vm state it also clears code area
