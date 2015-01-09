# C

## Sample Makefile

```
CC=clang
CFLAGS=-Weverything
LDFLAGS=
SOURCES=hello.c
OBJECTS=$(SOURCES:.c=.o)
EXECUTABLE=hello

all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS)
	$(CC) $(LDFLAGS) $(OBJECTS) -o $@

.c.o:
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -rf *.o $(EXECUTABLE)
```

## Guaranteed data type sizes

Portable types such as `uint16_t` (unsigned integer, 16 bits) allow data type sizes to be guaranteed across platforms and are defined in `stdint.h`.

`stdint.h` is only guaranteed to exist in C99 onwards.

## Compiler options

 * `-D`: Define this macro - e.g. `-D_BSD_SOURCE` is the same as including `#define _BSD_SOURCE 1`.

## GCC warning flags

 * `-Wall`: Enables a large number of warnings, though not all (despite the name).
 * `-Wextra`: Enables extra warnings above and beyond `-Wall`.
 * `-Werror`: Make all warnings into errors. Effectively this means that code which produces warnings will fail to compile.

## Clang warning flags

Clang supports most GCC warning flags, as well as some extras.

 * `-Weverything`: All warnings, may include new warnings in future versions (so code may compiler under `-Weverything` now but not if clang is upgraded).

## Changes from C89 to C99

 * Support for C++ style single-line comments, i.e. `// this is a comment`.
 * Variables no longer have to be declared before code, e.g. `for (int i = 0; i < 9, i++)`.
 * Support for variable length arrays, e.g. `int a[b][c]`.
 
## Embedded C

 * Declaring a variable as `const` will cause it to be stored in the program code space rather than the limited variable storage space (e.g. RAM)
 * Use the `volatile` keyword for pointers to memory-mapped registers, and global variables that are shared between threads.

When laying out structs, order members in descending order of size. For example:

```
struct abc
{
  char a; /* 1 byte */
  short b; /* 2 bytes */
  char c[5]; /* 5 bytes */
};
```

should be restructured as:

```
struct abc
{
  char c[5]; /* 5 bytes */
  short b; /* 2 bytes */
  char a; /* 1 byte */
};
```

## Links

 * [The Lost Art of C Structure Packing](http://www.catb.org/esr/structure-packing/)
 * [Memory management in C programs](http://nethack4.org/blog/memory.html)
 * [Building C Projects](http://nethack4.org/blog/building-c.html)
 * [Deep C](http://www.slideshare.net/olvemaudal/deep-c)
 * [To Become a Good C Programmer](http://fabiensanglard.net/c/index.php)
 * [C11 atomic variables and the kernel](http://lwn.net/Articles/586838/)
 * [The Definitive C Book Guide and List](http://stackoverflow.com/questions/562303/the-definitive-c-book-guide-and-list)
 * [C: The Complete Nonsense](http://www.seebs.net/c/c_tcn4e.html) - Critique of Herbert Schildt's _C: The Complete Reference_.
 * [The Annotated Annotated C Standard](http://www.davros.org/c/schildt.html)
 * [CProgramming.com](http://www.cprogramming.com/)
 * [comp.lang.c FAQ](http://c-faq.com/)
 * [The Descent to C](http://www.chiark.greenend.org.uk/~sgtatham/cdescent/)
 * [MSC06-CPP](https://www.securecoding.cert.org/confluence/display/cplusplus/MSC06-CPP.+Be+aware+of+compiler+optimization+when+dealing+with+sensitive+data) - CERT article on why your compiler might optimise away security functions.
 * [Does using SecureZeroMemory() really help to make the application more secure?](http://stackoverflow.com/questions/786093/does-using-securezeromemory-really-help-to-make-the-application-more-secure) - StackOverflow question, with some useful pointers in the answers.
 * [Setting variable to NULL after free](http://stackoverflow.com/questions/1025589/setting-variable-to-null-after-free) - StackOverflow thread on avoiding dangling pointers.
 * [Open source development using C99](http://www.ibm.com/developerworks/library/l-c99/index.html)
 * [Use of C99 Variable Length Arrays](http://msdn.microsoft.com/en-us/library/zb1574zs%28v=VS.100%29.aspx) - Workaround for the fact that Visual C++ doesn't support variable length arrays.
 * [The Top 10 Ways to get screwed by the "C" programming language](http://www.andromeda.com/people/ddyer/topten.html) - Some mistakes to avoid.
 * [Linus Torvalds on Why C++ is a horrible language and C is the only sane choice](http://lwn.net/Articles/249460/)
 * [A response to Linus Torvalds on C++](http://warp.povusers.org/OpenLetters/ResponseToTorvalds.html)
 * [What Is C For?](http://www.informit.com/articles/article.aspx?p=1211715&rll=1)
 * [Writing Insecure C, Part 1](http://www.informit.com/articles/article.aspx?p=1249297&rll=1)
 * [Writing Insecure C, Part 2](http://www.informit.com/articles/article.aspx?p=1249298&rll=1)
 * [Writing Insecure C, Part 3](http://www.informit.com/articles/article.aspx?p=1249299&rll=1)
 * [GCC Warning Options](http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html) - The various warning options available in the `gcc` compiler.
 * [The Development of the C Language](http://cm.bell-labs.com/cm/cs/who/dmr/chist.html) - History of the C language and its development, by Dennis Ritchie (the 'R' in 'K&R').
