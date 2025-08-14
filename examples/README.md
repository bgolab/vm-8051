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
