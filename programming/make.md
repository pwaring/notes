# Make

## Filenames

Makefiles can be called `makefile`, `Makefile` or `GNUMakefile`. Other names
can be used, but require the `-f ` flag to be passed when invoking the `make`
command.

## Basic rules

A makefile consists of a set of rules, split into the target, prerequisites and
commands. Make will attempt to build the first target - the default - if no
target is specified on the command line.

```
target: prereq1 prereq2
	commands
```

The commands section must be preceded by a tab, not spaces.

An example for compiling a C source file which also requires a header into an
object file might be:

```
hello.o: hello.c hello.h
	gcc -c hello.c
```

Effectively, this rule says: If the contents of `hello.c` or `hello.h` have
changed (i.e. any prerequisites have been modified more recently than the
target), `hello.o` needs to be rebuilt, using the command `gcc -c hello.c`.

Note that although `gcc` does not need to know about `hello.h`, because it will
pick up the relationship when compiling `hello.c`, `make` does need a hint,
otherwise any changes to `hello.h` will not force the object file to be rebuilt.

A rule does not have to be defined on a single line. Each time `make` encounters
a target, it adds the prerequisites to the dependency graph. For example, the
following rules are identical:

```
hello.o: hello.c hello.h
	gcc -c hello.c
```

```
hello.o: hello.h
hello.o: hello.c
	gcc -c hello.c
```

Wildcards can be used like so:

```
program: *.c
	$(CC) -o $@ $^
```

Be careful with wildcards, as they can have unintended effects. For example, the
rule above will compile all files ending in `.c` in the current directory. If a
new `.c` file is added - intentionally or otherwise - it will be compiled and
linked into `program`.

Wildcards in targets and prerequisites are expanded by `make`, whereas those in
commands are expanded by the spawned subshell at the point of execution.

## Special targets and rules

The `.PHONY` rule can be used to mark targets that don't generate filesystem
objects. For example: `.PHONY: clean`.

## Built-in variables

`$@`: Full target filename to be built.

`$*`: Target filename without the suffix.

`$<`: File which caused the target to be made.

## Defining variables

To set a variable if it has not already been defined, use the `?=` operator:

```
REBUILD ?= no
```

## Sub-shell environments

The environment used by `$(shell)` is identical to the one used when `make` was
started.

## Useful command line options

`-n`: Tells `make` to display the commands it would execute, without actually
executing them.

## Parallel builds

If a Makefile has been written with parallelism in mind, it is possible to tell
`make` to build in parallel using the following option:

`-j [number of parallel builds]` or `--jobs=[number of parallel builds]`

If GNU Make 4.0 or later is available, the `--output-sync` option will keep the
output syncronised, otherwise the output will be sorted based on the order of
execution, which can make debugging difficult.

Problems which may occur when building in parallel:

 * Missing dependencies.

## Sample C++ Makefile

```
CC=clang++
CFLAGS=-Weverything -std=c++11 -stdlib=libc++
LDFLAGS=
SOURCES=readfile.cpp
OBJECTS=$(SOURCES:.cpp=.o)
EXECUTABLE=readfile

all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS)
	$(CC) $(LDFLAGS) $(OBJECTS) -o $@

.cpp.o:
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -rf *.o $(EXECUTABLE)
```
