# Post ideas

## Writing Perl modules using Dist::Zilla

## Output buffering in Perl

```
use IO::Handle;                                                                 
STDOUT->autoflush(1);
```

Useful for when you want a logfile to be updated with every write (e.g. when running tee or tail).
