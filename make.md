Make
====

A makefile consists of a set of rules, split into the target, prerequisites and commands.

```
target: prereq1 prereq2
	commands
```

The commands section must be preceded by a tab, not spaces.

An example for compiling a C source file which also requires a header into an object file might be:

```
hello.o: hello.c hello.h
	gcc -c hello.c
```

Effectively, this rule says: If the contents of `hello.c` or `hello.h` have changed, `hello.o` needs to be rebuilt, using the command `gcc -c hello.c`.

Note that although `gcc` does not need to know about `hello.h`, because it will pick up the relationship when compiling `hello.c`, `make` does need a hint, otherwise any changes to `hello.h` will not force the object file to be rebuilt.


