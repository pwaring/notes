# Ubuntu packaging

Installation of tools:

```
sudo apt-get install packaging-dev
```

Create GPG key (use RSA and 4096 bits):

```
gpg --gen-key
```

Find key ID (part after / on pub line):

```
gpg --list-keys
```

Send key to Ubuntu server:

```
gpg --send-keys --keyserver keyserver.ubuntu.com [KEY ID]
```

Set up pbuilder:

```
pbuilder-dist [release] create
```
