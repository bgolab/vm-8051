# vm-8051
stack-based vm for 8051
---
I recently discovered modern STC 8051 MCU versions in many popular DIY kits, and decided to implement a kind of toy vm. 

To simplify things and be able to fit the binary in constrained evironment the stack-based architecture was selected.
Stack-based architectures assumes RPN-like ISA design (we put data on data stack, we call a function which will consume the data and will return the resulst alaso on the stack).
To make stack-machine vm more usable I added couple of registers;)

What is modern 8051: 
apart from having hw feature non-existent in the 80-ies like I2C, SPI it also uses flash memory, and has built-in flash programmer using UART to transfer and spark flashing process.

Current assumptions:
- UART is used to enter commnads, both OS-like and VM language mnemonics,
- the commands will be parsed immediatelly, the OS-like commands will be executed, the VM commands will be tokenized & compiled to binary form
- STC8G1K08A and STC15W50AS chips will be used but I assume very generic ISA, and capabilities allowing to access any SFR register and XDATA memory (including internal one).
- Keil C51 will be used for the development

The hardware:
![alt text](https://github.com/bgolab/vm-8051/blob/main/manuals/ffaf2857487eb17f00f6ba5ee441.jpg)

To be updated...
