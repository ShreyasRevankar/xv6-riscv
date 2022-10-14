# Enhancing XV-6

xv6 is a simplified operating system developed at MIT. Its main purpose is to explain the main concepts of the operating system by studying an example kernel. The following specifications are the enhancements that have made to the xv6 kernel.

## Specification 1: System Calls

### Part 1: Strace

Modificatons made:

1. Makefile: Added `$U/_strace\` to UPROGS
2. proc.h: Added a variable `int mask` 
3. proc.c : Added `np->mask = p->mask;` to fork funtion
4. syscall.c: 
    + Added `extern uint64 sys_trace(void);``
    + Added `[SYS_trace] sys_trace` under syscall mapping fucntion
    + Created 2 arrays `nargs[]` and `sysnames` to map number o of arguments and index to system call name respectively
    + Modified `syscall` function to print process id, system call name, arguments and return value
5. sysproc.c: Added `sys_trace(void)` which acts a handler for trace system call
6. syscall.h: `#define SYS_trace 24`
7. user.h: `int trace(int);`
8. strace.c: Created a new file to test the trace system call in Users
9. usys.pl: `entry("trace");` 




