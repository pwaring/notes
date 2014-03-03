# C

## Compiler options

 * `-D`: Define this macro - e.g. `-D_BSD_SOURCE` is the same as including `#define _BSD_SOURCE 1`.

## GCC warning flags

 * `-Wall`: Enables a large number of warnings, though not all (despite the name).
 * `-Wextra`: Enables extra warnings above and beyond `-Wall`.
 * `-Werror`: Make all warnings into errors. Effectively this means that code which produces warnings will fail to compile.

## Changes from C89 to C99

 * Support for C++ style single-line comments, i.e. `// this is a comment`.
 * Variables no longer have to be declared before code, e.g. `for (int i = 0; i < 9, i++)`.
 * Support for variable length arrays, e.g. `int a[b][c]`.

## Links

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
