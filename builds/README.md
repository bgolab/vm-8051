WARNING: The development is still in the alpha stage - the features may change from build to build without notice

Release notes:

- v0.3B1 

HW: STC8G1K08A

Fixed: i#1:clear vm state before start; 

Features: 's' - added ver/pc info; z; supported small/capital letters in commands; added % / -- / ++ / ~ / Tx / N Tx = commands; ESC to break program

Refactoring: interpreter-BIG changes; 

- v0.3B2 

HW :STC8G1K08A; 

Fixed: i#3:ift broken; i#4:'g'vs g.reg conflict;

Features: 'g'->'x'; 'r' / 's' - vtimer support; new syntax: PR / PTx, IF, IFBRK / IFCNT, Lx w/o ':' 

Refactoring: jsr / ret, brk / cnt / vtimer, Lx;

- v0.4B1 - is being tested now
  
HW: STC8G1K08A; 

Fixed: i#5:str to accept spaces; i#6:unlimited str; i#7:isa-search to skip PRS; i#8:code size to not increased by xdata size; 
			 i#9:avoid os-cmd tokenization as bytecode; i#10:digit followed by letters parsed as NUM; i#11:ESC leaves 27 in buf;

Features: tokenizer(separated str/key/num in buf by 0; str w/ spaces; pshn8); interpreter(perf); PRC->.c/.x; 1kB xdata support; err/test-handling; 
			 3-char-labels with ':'; 's' to show only tokenized code; tokenizer tracing('t');

Refactoring: many
