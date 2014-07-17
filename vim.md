# Vim

 * `noh`: Remove all highlights.
 * `autoindent`: Automatically indent code as you type.
 * `cindent`: Indent C-style code.
 * `expandtab`: Expand tabs to spaces.
 * `shiftwidth=X`: Set tab width to X spaces.
 * `softtabspot=X`: Set tab width to X spaces.

## Insert command output

To insert the output of a command into the current buffer:

```
:r ! <command>
:r ! ls -l
```
