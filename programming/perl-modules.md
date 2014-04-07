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

'A distribution is a collection of metadata and one or more modules which forms a single redistributable, testable, and installable unit' (Modern Perl).

Things to remember
------------------

 * Package files must always end with `1;`, since the last evaluated statement is the return value. Effectively this says `return true;`, except Perl does not have a built-in boolean data type.
 * The `package` statement is block or file scoped. By keeping each package in an individual file, you can ensure that all packages are file scoped and not have to worry about the differences.
 * There is no concept of private subroutines in Perl. However, a subroutine beginning with an underscore is considered by convention to be private.

Module::Starter
---------------

`Module::Starter` helps set up a skeleton module directory tree through the `module-starter` command.

To avoid having to specify certain arguments each time you run `module-starter`, first create a file `$HOME/.module-starter/config` and add the following lines:

```
author: Your Name
email: your@email.address
builder: Module::Build
verbose: 1
```

Creating a new module is then as simple as running:

    module-starter --module=Module::Name

You can also include multiple modules in your distribution:

    module-starter --module=Module::Name,Module::Name::Something

The `Makefile.PL` file contains some metadata about the distribution. The most important option is `PREREQ_PM`, which is a hash of the Perl modules which are a prerequisite for this distribution - i.e. if you install the distribution via CPAN, it will automatically install these prerequisites first.

You can build a distribution by running:

    perl Makefile.PL && make && make test && make dist

If you want to use `Module::Build`, pass the `-mb` command when creating a module:

    module-starter --module=Module::Name,Module::Name::Something -mb

Or specify `builder: Module::Build` in your configuration file.

Building a distribution in this way can be done with the following command:

    perl Build.PL && ./Build && ./Build test && ./Build dist

Some of the tests require the following modules:

```
Test::Pod
Test::Pod::Coverage
```

Dist::Zilla
-----------

[Dist::Zilla](http://dzil.org/) is a collection of modules which aims to automate the boring parts of packaging - especially those which you might forget (e.g. creating a `MANIFEST`).

The first time you run Dist::Zilla, you have to set up some configuration variables:

    $ dzil setup

Creating a skeleton module is simple:

    $ dzil new Module::Name

Open `lib/Module/Name.pm`

Links
-----

 * [PrePAN](http://prepan.org/) - Get feedback on a module before submitting it to CPAN.
 * [Chapter 11. Packages and Modules](http://ofps.oreilly.com/titles/9781118013847/packages_and_modules.html) - From *Beginning Perl* (Wrox).
 * [Version numbers should be boring](http://www.dagolden.com/index.php/369/version-numbers-should-be-boring/) - How to properly define version numbers in Perl modules (no idea if this is authoritative).
