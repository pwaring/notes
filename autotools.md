# Autotools

Each individual command under a rule is executed in its own shell, so a variable exported in one command will not be available in others.

The first target in a Makefile is the default and will be used if make is run without any arguments.

## Phony targets

Phony targets are labelled as such:

```
.PHONY all clean
```

They do not refer to true products, but rather to outcomes or actions. Marking targets as phony tells make not to look for filesystem objects with the same name.

