- Code examples (small and capital letters accepted):
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

- other examples from performance testing

"'+/*: ' 32000 PT0 1 30001 DO 1 2 + DROP 3 4 * DROP LOOP 32000 T0 - . CR", 

"'DL:' 32000 PT0 1 30001 DO LOOP 32000 T0 - . CR",

"'+:' 32000 PT0 1 30001 DO 1 2 + DROP LOOP 32000 T0 - . CR", 

"'A/PA:' 32000 PT0 1 30001 DO A PA LOOP 32000 T0 - . CR", 	

"'MR:' 32000 PT0 0 1 30001 DO MR LOOP 32000 T0 - . CR", 

"'DUP/DRP:' 32000 PT0 1 30001 DO DUP DROP LOOP 32000 T0 - . CR", 

"'S:' 0x80 7 SW 0x80 SR . ',' 0xD1 77 SW 0xD1 SR . CR", 											// SFR+HEX 					(out: S:7,77; P0: 0000111)

"'X:' 0 0xB DO I MR . ',' LOOP CR", 																					// XDATA 						(out: 

X:69,0,1,69,0,5...)

"'R:' 0xF0 PA A 0xFFFF + . CR",																								// REG+HEX					(out: R:239)

"1 5 DO I 3 == IFCNT I . ':' JSR PR ',' LOOP HLT PR: 1 5 DO I . LOOP RET",	// DO/IFT/CNT/nest 	(out: 1:1234,2:1234,4:1234)
