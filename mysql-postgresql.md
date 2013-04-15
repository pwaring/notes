MySQL to PostgreSQL
===================

Simple script for creating `Result` classes from an existing MySQL database. Taken from `DBIx::Class::Schema::Loader` documentation, with corrections:

```
#!/usr/bin/perl

use Modern::Perl;
use DBIx::Class::Schema::Loader qw/ make_schema_at /;

make_schema_at(
  'DB::Schema',
  { debug => 1, dump_directory => './lib' },
  [ 'dbi:mysql:dbname=database', 'username', 'password'
  ],
);
```

Useful links
------------

 * [py-mysql2pgsql](https://github.com/philipsoutham/py-mysql2pgsql) - Python module for converting MySQL to PostgreSQL. Didn't work for me, but that may be due to my lack of Python knowledge and not having all the dependencies.
 * [How to make a proper migration from MySQL to PostgreSQL](http://wiki.postgresql.org/wiki/How_to_make_a_proper_migration_from_MySQL_to_PostgreSQL) - From 2009, so generic advice is useful but other parts may be out of date.
 * [Converting from other Databases to PostgreSQL](http://wiki.postgresql.org/wiki/Converting_from_other_Databases_to_PostgreSQL) - Starting point for jumping off to other sites.
 * [MySql to PostgreSql migration](http://stackoverflow.com/questions/4756825/mysql-to-postgresql-migration)
 * [Switching from MySQL to PostgreSQL - tips, tricks and gotchas?](http://stackoverflow.com/questions/772111/switching-from-mysql-to-postgresql-tips-tricks-and-gotchas) - Good list of things to watch out for.
 * [How different is PostgreSQL to MySQL?](http://stackoverflow.com/questions/724867/how-different-is-postgresql-to-mysql)
 * [Migrate from MySQL to PostgreSQL on Linux (Kubuntu)](http://stackoverflow.com/questions/2831009/migrate-from-mysql-to-postgresql-on-linux-kubuntu/2831517)
 * [Migrating from MySQL to PostgreSQL](http://www.xach.com/aolserver/mysql-to-postgresql.html)
 * [Converting MySQL to PostgreSQL](http://en.wikibooks.org/wiki/Converting_MySQL_to_PostgreSQL)

