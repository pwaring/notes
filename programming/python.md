# Python

 * Every file of Python source code that ends in .py is a module - no special code or naming is required.
 * `dir` fetches all names available inside a module: `dir(modname)`
 * Each file is a self-contained namespace.
 * reloads are not transitive, so reloading module A which imports module B does not reload B.
 * To run a script: `exec(open('script.py').read())`
