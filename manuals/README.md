WARNING: This part will often change, some parts of manual might be oudate as the development is in the early stage

- Early draft of the manual (0.4B1 version):

-notes: watch out name-conflict(label vs os/reg/timer); RPN-like; HLT=0(exit, separate code from subroutines, only SINGLE HLT so separate all procedures in one place following HLT!); infinite-loop->JMP; RSTACK for JSR/DL/loop-counters; watch/clean D/RSTACK!; int16(-32k...32k)

-os:					[s]tate, [z]eroize(state&code), e[x]ec, [t]race, [ESC]break

-flow:				(M N)DO, I, (N)IFBRK|IFCNT, LOOP(M...N-1, nesting); label(3-char followed by ':'); (N)IFJMP; JMP|JSR label(no ':'); RET; HLT(exit)

-print/input:	'str'(string), (N).c(char), (N).(dec), (N).x(hex); CR(new line); KEY(blocking))

-math:	+, -, *, /, %, &, |, ^, ==, <>, >, >=, <, <=, --, ++, ~

-stack:	DUP, DROP, SWAP, RPSH, RPOP, RDROP, RFETCH, N | 0xH-HHHH(hex)(N->stack), r(N), e.g. A(A->stack), (N)PR, e.g. 7 PA(stack->A), reg: A-H

-mem:		(a)MR; (a v)MW (XDATA/XSFR); (a)SR; (a v)SW (SFR); a-addr, v-val

-timer:	Tx(N), e.g. T0(T0->stack); (N)PTx, e.g. 90 PT0(90->T0); no-autoload, countdown, max 32s<int, 1ms unit, x=0-3

- Runtime error codes + token types (as reported when tracing enabled) :

#define MISSING_LAB		"e:mLAB"

#define MISSING_LOOP	"e:mLOOP"

#define MISSING_ARG		"e:mARG"

#define BAD_HEX				"e:bHEX"

#define BAD_NUM				"e:bNUM"

#define BAD_CMD				"e:bCMD"

#define BAD_LEN 			"e:bLEN"

#define BAD_LAB				"e:bLAB"

#define DS_OVERFLOW		"e:DSo"

#define DS_UNDERFLOW	"e:DSu"

#define RS_OVERFLOW		"e:RSo"

#define RS_UNDERFLOW	"e:RSu"

#define	T_NUM					"NUM"

#define	T_STR					"STR"

#define	T_KEY					"KEY"

#define	T_LAB					"LAB"
