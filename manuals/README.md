WARNING: This part will often change, some parts of manual might be oudate as the development is in the early stage

- Very draft stage of the manual (here 0.3B2 version):

-OS:					[s]tate / [r]reset(state) / [z]eroize(state&code), e[x]ecute / [t]race, ESC-break

-flow: 				(M N)DO; I; (N)IFBRK|IFCNT; LOOP (M...N-1, nesting), Lx(label), (N)IF | JMP | JSR Lx, RET, HLT(exit)

-i/o: 				'str'(print), (N).c(print as char, (N).(print as int), (N).x(print as hex); CR, KEY(K) or SBUF(non-block) or KEY(non-block w/ SBUF internally)?

-math:				+, -, *, /, %, &, |, ^, ==, <>, >, >=, <, <=, --, ++, ~, takes arg(s) from stack and returns back result

-stack-num:		DUP, DROP, SWAP, RPSH, RPOP, RDROP, RFETCH, N/0xH-HHHH(hex)-on stack

-stack-mem:		(addr)MR / (addr val)MW (XDATA/XSFR); (addr)SR / (addr val)SW (SFR); sbit-BR/BW?

-stack-reg:		R(N), e.g. A (A on stack); (N) PR, e.g. 1 PA (load 1 to A); R: A-H

-vtimer: 			Tx(N), e.g. T0; (N) PTx, e.g. 90 PT0 (inits PT0 w/ 90); no-autoload, countdown, max 32s<int, 1ms unit, x=0-3;

- Very draft stage of the manual (here 0.4B1 version):

-os:		[s]tate, [r]reset(state), [z]eroize(state&code), e[x]ec, [t]race, [ESC]break

-flow:	(M N)DO, I, (N)IFBRK|IFCNT, LOOP(M...N-1, nesting); label(3-char followed by ':'); (N)IF|JMP|JSR label(no ':'); RET; HLT(exit)

-print:	'str'(string), (N).c(char), (N).(dec), (N).x(hex); CR(new line)

-input:	KEY(blocking)); SBUF(non-blocking)

-math:	+, -, *, /, %, &, |, ^, ==, <>, >, >=, <, <=, --, ++, ~

-stack:	DUP, DROP, SWAP, RPSH, RPOP, RDROP, RFETCH, N | 0xH-HHHH(hex)(N->stack), r(N), e.g. A(A->stack), (N)PR, e.g. 7 PA(stack->A), reg: A-H

-mem:		(a)MR; (a v)MW (XDATA/XSFR); (a)SR; (a v)SW (SFR); a-addr, v-val

-timer:	Tx(N), e.g. T0(T0->stack); (N)PTx, e.g. 90 PT0(90->T0); no-autoload, countdown, max 32s<int, 1ms unit, x=0-3

- Runtime error codes + token types (as reported when tracing enabled) :

#define NO_LAB				"nLAB"

#define NO_LOOP				"nLOOP"

#define NO_ARG				"nARG"

#define BAD_HEX				"bHEX"

#define BAD_NUM				"bNUM"

#define BAD_CMD				"bCMD"

#define BAD_LEN 			"bLEN"

#define BAD_LAB				"bLAB"

#define DS_OVERFLOW		"oDS"

#define DS_UNDERFLOW	"uDS"

#define RS_OVERFLOW		"oRS"

#define RS_UNDERFLOW	"uRS"

#define	T_NUM					"NUM"

#define	T_STR					"STR"

#define	T_KEY					"KEY"

#define	T_LAB					"LAB"
