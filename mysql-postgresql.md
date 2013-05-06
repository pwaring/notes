MySQL to PostgreSQL
===================

Simple script for creating `Result` classes from an existing MySQL database, then producing a PostgreSQL schema file from those classes:

```
#!/usr/bin/perl

use Modern::Perl;
use DBIx::Class::Schema::Loader qw/ make_schema_at /;

my $dsn = 'dbi:mysql:dbname=database';
my $user = '';
my $pass = '';

make_schema_at(
  'MyDB::Schema',
  { debug => 1, dump_directory => './lib' },
  [ $dsn, $user, $pass
  ],
);

my $schema = MyDB::Schema->connect($dsn, $user, $pass);
$schema->create_ddl_dir(['PostgreSQL'], '0.1', './', undef, { add_drop_table => 0 });
```

Pre-migration checks
--------------------

Two ways of testing to see whether data needs to be cleaned up before migrating:

 1. Quick scan of tables for obvious 'bad' values (e.g. DATE columns with '0000-00-00') using WHERE clauses - i.e. a blacklist.
 2. Exhaustive checks of every row - i.e. a whitelist.

Probably also a good idea to check foreign key relationships which have not explicitly been defined by the use of `REFERENCES`.

Reasons for pre-migration checks include:

  * MySQL is not as strict as PostgreSQL about validating data (or at least, not with the default MySQL configuration).
  * MySQL will usually enforce referential integrity if foreign keys are explicitly defined, but not all developers add the relevant `REFERENCES` constraints to their schemas.
 * Easier to identify and fix bad data whilst still using MySQL, and having a clean data set should make migration smoother.

Useful links
------------

 * [py-mysql2pgsql](https://github.com/philipsoutham/py-mysql2pgsql) - Python module for converting MySQL to PostgreSQL. Did not work for me, but that may be due to my lack of Python knowledge and not having all the dependencies.
 * [How to make a proper migration from MySQL to PostgreSQL](http://wiki.postgresql.org/wiki/How_to_make_a_proper_migration_from_MySQL_to_PostgreSQL) - From 2009, so generic advice is useful but other parts may be out of date.
 * [Converting from other Databases to PostgreSQL](http://wiki.postgresql.org/wiki/Converting_from_other_Databases_to_PostgreSQL) - Starting point for jumping off to other sites.
 * [MySql to PostgreSql migration](http://stackoverflow.com/questions/4756825/mysql-to-postgresql-migration)
 * [Switching from MySQL to PostgreSQL - tips, tricks and gotchas?](http://stackoverflow.com/questions/772111/switching-from-mysql-to-postgresql-tips-tricks-and-gotchas) - Good list of things to watch out for.
 * [How different is PostgreSQL to MySQL?](http://stackoverflow.com/questions/724867/how-different-is-postgresql-to-mysql)
 * [Migrate from MySQL to PostgreSQL on Linux (Kubuntu)](http://stackoverflow.com/questions/2831009/migrate-from-mysql-to-postgresql-on-linux-kubuntu/2831517)
 * [Migrating from MySQL to PostgreSQL](http://www.xach.com/aolserver/mysql-to-postgresql.html)
 * [Converting MySQL to PostgreSQL](http://en.wikibooks.org/wiki/Converting_MySQL_to_PostgreSQL)

