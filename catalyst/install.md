# Catalyst Installation

Using `local::lib`:

```
perl -MCPAN -Mlocal::lib -e 'CPAN::install(Catalyst::Devel)'
perl -MCPAN -Mlocal::lib -e 'CPAN::install(Catalyst::Runtime)'
```

Without `local::lib`:

```
perl -MCPAN -e 'install Catalyst::Runtime'
perl -MCPAN -e 'install Catalyst::Devel'
```


