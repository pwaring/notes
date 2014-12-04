# Assembly

## Syntax

Two main x86 assembly syntax:

 * AT&T: Lots of $ and % symbols. Default for most disassembly tools on Linux.
 * Intel: Cleaner and easier to read, requires the `-M intel` command line option to `objdump`.

## Generating Assembly from C

Generating assembly: Use the `-S` flag in gcc or clang, e.g. `gcc -S foo.c` produces `foo.s`.

Comparison expression in C, such as `i < 10` (in a `for` loop), appear to be translated to different assembly by different compilers, and not necessarily what you would expect.

GCC:

```
cmpl	$9, -4(%rbp)
jle	.L3
```

'if i <= 9, jump to the beginning of the loop'.

clang:

```
cmpl	$10, -8(%rbp)
jge	.LBB0_4
```

'if i >= 10, jump to the code block after the loop'.

Neither compiler compares the integer `10` with the contents of `i`. Although the approaches taken by the compilers are functionally identical, it is interesting that they have both decided to generate assembly with different logic to the original code, yet in two different ways.

Furthermore, in both cases the compiler does not compile the `i++` statement within the `for` loop to an `inc` command, contrary to what most C programming books would claim. Possibly the case that the difference between `inc` and `add` is non-existant on modern processors, or that the processor itself will automatically treat `inc (source)` and `add $1, (source)` the same.

## Registers

16-bit registers: AX, BX, CX, DX, FLAGS

32-bit registers: EAX (Extended AX), EFLAGS etc.

64-bit registers: RAX etc.

Named registers:

 * EAX: Accumulator
 * EBX: Base
 * ECX: Counter
 * EDX: Data
 * ESP: Stack Pointer
 * EBP: Base Pointer
 * ESI: Source Index
 * EDI: Destination Index
 * EIP: Instruction Point


## Links

 * [Software optimization resources](http://www.agner.org/optimize/)
 * [Intel x86 JUMP quick reference](http://www.unixwiz.net/techtips/x86-jumps.html)
 * [PC assembly language tutorial](http://www.drpaulcarter.com/pcasm/)
