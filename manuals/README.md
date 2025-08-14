WARNING: This part will often change, some parts of manual might be oudate as the development is in the early stage

Very draft stage of the manual:
-OS:					[s]tate / [r]reset(state) / [z]eroize(state&code), e[x]ecute / [t]race, ESC-break

-flow: 				(M N)DO; I; (N)IFBRK|IFCNT; LOOP (M...N-1, nesting), Lx(label), (N)IF | JMP | JSR Lx, RET, HLT(exit)

-i/o: 				'str'(print), (N).c(print as char, (N).(print as int), (N).x(print as hex); CR, KEY(K) or SBUF(non-block) or KEY(non-block w/ SBUF internally)?

-math:				+, -, *, /, %, &, |, ^, ==, <>, >, >=, <, <=, --, ++, ~, takes arg(s) from stack and returns back result

-stack-num:		DUP, DROP, SWAP, RPSH, RPOP, RDROP, RFETCH, N/0xH-HHHH(hex)-on stack

-stack-mem:		(addr)MR / (addr val)MW (XDATA/XSFR); (addr)SR / (addr val)SW (SFR); sbit-BR/BW?

-stack-reg:		R(N), e.g. A (A on stack); (N) PR, e.g. 1 PA (load 1 to A); R: A-H

-vtimer: 			Tx(N), e.g. T0; (N) PTx, e.g. 90 PT0 (inits PT0 w/ 90); no-autoload, countdown, max 32s<int, 1ms unit, x=0-3;
