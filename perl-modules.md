Perl Modules
============

Skeleton module
---------------

Most basic package is:

```
package MyPackage;

use strict;
use warnings;
use autodie;

our $VERSION = 0.01;

1;
```

'A module is simply a file that contains one or more packages, though it’s generally recommended to have one package per module.' (Beginning Perl).

Things to remember
------------------

 * Package files must always end with `1;`, since the last evaluated statement is the return value. Effectively this says `return true;`, except Perl does not have a built-in boolean data type.

Links
-----

 * [Chapter 11. Packages and Modules](http://ofps.oreilly.com/titles/9781118013847/packages_and_modules.html) - From *Beginning Perl* (Wrox).
