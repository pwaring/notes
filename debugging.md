Debugging
=========

Viewing assembly code for an executable:

```
objdump -D for-nonblock | grep -A20 main.:
00000000004004f4 <main>:
  4004f4:	55                   	push   %rbp
  4004f5:	48 89 e5             	mov    %rsp,%rbp
  4004f8:	48 83 ec 20          	sub    $0x20,%rsp
  4004fc:	89 7d ec             	mov    %edi,-0x14(%rbp)
  4004ff:	48 89 75 e0          	mov    %rsi,-0x20(%rbp)
  400503:	c7 45 fc 00 00 00 00 	movl   $0x0,-0x4(%rbp)
  40050a:	eb 1b                	jmp    400527 <main+0x33>
  40050c:	b8 4c 06 40 00       	mov    $0x40064c,%eax
  400511:	8b 55 fc             	mov    -0x4(%rbp),%edx
  400514:	89 d6                	mov    %edx,%esi
  400516:	48 89 c7             	mov    %rax,%rdi
  400519:	b8 00 00 00 00       	mov    $0x0,%eax
  40051e:	e8 cd fe ff ff       	callq  4003f0 <printf@plt>
  400523:	83 45 fc 01          	addl   $0x1,-0x4(%rbp)
  400527:	83 7d fc 04          	cmpl   $0x4,-0x4(%rbp)
  40052b:	7e df                	jle    40050c <main+0x18>
  40052d:	c7 45 fc 00 00 00 00 	movl   $0x0,-0x4(%rbp)
  400534:	eb 1b                	jmp    400551 <main+0x5d>
  400536:	b8 4c 06 40 00       	mov    $0x40064c,%eax
  40053b:	8b 55 fc             	mov    -0x4(%rbp),%edx
```

Using Intel assembler (easier to read):

```
objdump -D for-nonblock -M intel | grep -A20 main.:
00000000004004f4 <main>:
  4004f4:	55                   	push   rbp
  4004f5:	48 89 e5             	mov    rbp,rsp
  4004f8:	48 83 ec 20          	sub    rsp,0x20
  4004fc:	89 7d ec             	mov    DWORD PTR [rbp-0x14],edi
  4004ff:	48 89 75 e0          	mov    QWORD PTR [rbp-0x20],rsi
  400503:	c7 45 fc 00 00 00 00 	mov    DWORD PTR [rbp-0x4],0x0
  40050a:	eb 1b                	jmp    400527 <main+0x33>
  40050c:	b8 4c 06 40 00       	mov    eax,0x40064c
  400511:	8b 55 fc             	mov    edx,DWORD PTR [rbp-0x4]
  400514:	89 d6                	mov    esi,edx
  400516:	48 89 c7             	mov    rdi,rax
  400519:	b8 00 00 00 00       	mov    eax,0x0
  40051e:	e8 cd fe ff ff       	call   4003f0 <printf@plt>
  400523:	83 45 fc 01          	add    DWORD PTR [rbp-0x4],0x1
  400527:	83 7d fc 04          	cmp    DWORD PTR [rbp-0x4],0x4
  40052b:	7e df                	jle    40050c <main+0x18>
  40052d:	c7 45 fc 00 00 00 00 	mov    DWORD PTR [rbp-0x4],0x0
  400534:	eb 1b                	jmp    400551 <main+0x5d>
  400536:	b8 4c 06 40 00       	mov    eax,0x40064c
  40053b:	8b 55 fc             	mov    edx,DWORD PTR [rbp-0x4]
```

Debugging a program:

```
gdb -q ./program
```

Useful commands within GDB:

 * `break main`: Break at the `main()` function.
 * `run`: Run the program to the next breakpoint.
 * `info registers`: Print contents of all registers.
 
Registers
---------

General purpose registers:

 * EAX - Accumulator
 * ECX - Counter
 * EDX - Data
 * EBX - Base

Mainly act as temporary registers for the CPU.

Other general purpose registers:

 * ESP - Stack Pointer
 * EBP - Base Pointer
 * ESI - Source Index
 * EDI - Destination Index

On 64-bit machines, 'E' is replaced with 'R', so RAX, RCX etc.
