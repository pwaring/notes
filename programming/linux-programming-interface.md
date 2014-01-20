Linux Programming Interface
===========================

 * `ctime()` marked as obsolete in SUSv3.
 * `gethostbyname()` and `gethostbyaddr()` removed in SUSv4.
 * Get information about version etc. of a shared library by running it as a command, e.g. `/lib/libc.so.6`.
 * `ldd <binary>` shows the library dependency list for a given binary.
 * Most standard system types are in `<sys/types.h>`.
 * `O_NOATIME` flag can be passed to the `open()` function - useful for indexing and backup programs as it reduces the amount of disk activity.
 * `truncate()` is the only system call which can change the contents of a file without first obtaining a file descripter (e.g. via `open()`).
