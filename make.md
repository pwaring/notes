Make
====

Filenames
---------

Makefiles can be called `makefile`, `Makefile` or `GNUMakefile`. Other names can be used, but require the `-f ` flag to be passed when invoking the `make` command.

Basic rules
-----------

A makefile consists of a set of rules, split into the target, prerequisites and commands. Make will attempt to build the first target - the default - if no target is specified on the command line.

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

Effectively, this rule says: If the contents of `hello.c` or `hello.h` have changed (i.e. any prerequisites have been modified more recently than the target), `hello.o` needs to be rebuilt, using the command `gcc -c hello.c`.

Note that although `gcc` does not need to know about `hello.h`, because it will pick up the relationship when compiling `hello.c`, `make` does need a hint, otherwise any changes to `hello.h` will not force the object file to be rebuilt.

Useful command line options
---------------------------

`-n`: Tells `make` to display the commands it would execute, without actually executing them.
