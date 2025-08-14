WARNING: This part will often change, some parts of manual might be oudate as the development is in the early stage

Very draft stage of the manual:

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
