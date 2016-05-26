# MySQL performance

## Profiling queries

Enable the profiler for this session (note this method is deprecated in later
versions of Percona):

`SET PROFILING = 1`

Run query:

`SELECT * FROM table`

Show the profiles (summary of query and time taken):

`SHOW PROFILES`

Show detailed information for a specific query:

`SHOW PROFILE FOR QUERY 1`

## Locking

Locking has a trade-off effect on performance. On the one hand, a high-level
lock (e.g. table lock) is cheap to obtain, but prevents reads and writes. A
row-level lock is more expensive to obtain, but allows reads and writes to other
rows.

In some circumstances, the locking strategy is fixed. For example, `ALTER TABLE`
commands will always require a table lock.

## Transactions

Transactions help to ensure that a collection of statements are executed as one
atomic commit. There is a cost to this, and it may not be required for all
applications.

## Storage engines

### MyISAM

MyISAM supports compressed tables using `myisampack`. Compressed tables use up
less disk space and therefore require fewer seeks to load. They may be a good
choice for read-only data, e.g. lookup tables.

The major downside to MyISAM is that it uses table locking, and therefore it is
not suitable for data which is regularly updated (e.g. sessions, logs).

### Converting between storage engines

The simplest and easiest way to convert a table to another storage engine is
with the `ALTER TABLE` command:

```
ALTER TABLE mytable ENGINE = 'InnoDB';
```

However, this performs a copy of each row in the table, and therefore is
unlikely to be suitable for live data.

## Data types

Some broad advice:

 * Simpler data types are easier to process.
 * Integers are cheaper to compare than strings.
 * Use integers for IP addresses.
 * Avoid NULL where possible as it is harder for MySQL to optimise queries which
 may involve NULL values.


## Joins

MySQL has a limit of 61 tables per join.

## Indexes

Adding a b-tree index to an InnoDB table:

`ALTER TABLE my_table ADD KEY (my_column)`
