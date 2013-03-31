Assembly
========

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
