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

OS-like commands:
- x (eXecute) - starts VM and runs programs
- s (show state) - good for debugging to reveal internal VM state (bytecode, data & return stacks, registers, etc)
- t (trace) - good for debugging to trace proxes of execution
- r (reset state) - to clear vm state
- z (zeroize) - apart from resetting the vm state it also clears code area
- ESC (breaks program) - actaually not a command but helpfull feature which allows to break running program

The stack-based vm language:

-flow: 				(M N) DO; I; (N)IFBRK; IFCNT; LOOP (M...N-1, nesting supported), Lx, (N)IF Lx, JMP Lx, JSR Lx / RET, HLT(exit)

-i/o: 				'str'(print string), (N)PRC, (N)., CR (new line), KEY(K) or SBUF(non-block) or KEY(non-block w/ SBUF internally)?

-math:				+, -, *, /, %, &, |, ^, ==, <>, >, >=, <, <=, --, ++, ~, takes arg(s) from stack and returns back result

-stack-num:		DUP, DROP, SWAP, RPSH, RPOP, RDROP, RFETCH, N/0xH-HHHH(hex)-on stack

-stack-mem:		(addr)MR / (addr val)MW (XDATA/XSFR); (addr)SR / (addr val)SW (SFR); sbit-BR/BW?

-stack-reg:		R(N), e.g. A (A on stack); (N) PR, e.g. 1 PA (load 1 to A); R: A-H

-vtimer: 			Tx(N), e.g. T0; (N) PTx, e.g. 90 PT0 (inits PT0 w/ 90); no-autoload, countdown, max 32s<int, 1ms unit, x=0-3;

Code examples (small and capital letters accepted):
1. DO LOOP
   
1 10 DO I . ',' I I * . CR LOOP

An explanation: for every value from 1 to 10 (exclusive) print value, separate by ',', print power of two of this value and move to new line).
Simple? Yeah, as Forth;)

2. Demonstrates SFR access: use watchdog to reboot VM
   
0xc1 0x20 SW

An explanation: 0x20 written at 0xc1 SFR enables watchdog so the vm reboots as we do not refresh the watchdog counter

3. Demonstrates virtual timers capabilities: blinking a LED connected between P5.5 and P5.4 (charlie plexing):

0xc8 PA L0 JSR L3 A 0x10 SW JSR L3 A 0 SW JMP L0 HLT 
L3 300 pt0 L1 t0 0 <> if L1 RET 

(the command buffer of 80 bytes is TOO short to fit this code so need to split it into at least two lines)

An explanation: it's an excercise to the reader

The hardware:
https://raw.githubusercontent.com/bgolab/vm-8051/refs/heads/main/Sad65bc710472466db1308be795e810dbz.webp

To be updated...
