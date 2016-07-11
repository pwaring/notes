# MySQL performance

## Connections

The MySQL protocol is half-duplex, which means that it can send or receive
messages, but not both at the same time.

## Query cache

Looking up an item in the query cache is a hash operation.

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

To clear out the query cache:

`RESET QUERY CACHE`

## Using EXPLAIN

A simple test to see if indexes are being used:

`EXPLAIN SELECT * FROM table WHERE column = ?`

If the `rows` value returned is significantly higher than the number of rows
fetched by the query and the `type` value is `ALL` then it is likely that MySQL
is performing a full table scan. Adding an index can significantly reduce the
number of rows scanned  (though not always down to 1:1 scanned:fetched).

If the `extra` value is `Using where` then this also suggests that MySQL is
discarding rows after scanning them, which may have performance implications.

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

To find the storage engine for a given table:

```
SELECT engine FROM information_schema.tables
WHERE
  table_schema = 'database'
  AND table_name = 'table'
```

Storage engines for all tables in a given database:

```
SELECT table_name, engine FROM information_schema.tables
WHERE
  table_schema = 'database'
```

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
