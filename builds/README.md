WARNING: The development is still in the alpha stage - the features may change from build to bild without notice

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

