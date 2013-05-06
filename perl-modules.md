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
 * The `package` statement is block or file scoped. By keeping each package in an individual file, you can ensure that all packages are file scoped and not have to worry about the differences.
 * There is no concept of private subroutines in Perl. However, a subroutine beginning with an underscore is considered by convention to be private.

Dist::Zilla
-----------

Dist::Zilla is a collection of modules which aims to automate the boring parts of packaging - especially those which you might forget.

The first time you run Dist::Zilla, you have to set up some configuration variables:

    $ dzil setup

Creating a skeleton module is simple:

    $ dzil new Module::Name



Links
-----

 * [Chapter 11. Packages and Modules](http://ofps.oreilly.com/titles/9781118013847/packages_and_modules.html) - From *Beginning Perl* (Wrox).
 * [Version numbers should be boring](http://www.dagolden.com/index.php/369/version-numbers-should-be-boring/) - How to properly define version numbers in Perl modules (no idea if this is authoritative).
