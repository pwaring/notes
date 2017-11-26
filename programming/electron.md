# Electron

## Creating a new project

Run the following commands:

```
npm init
npm install electron --save-dev --save-exact
npm install electron_rebuild --save-dev
```

Run the project using:

```
./node_modules/.bin/electron .
```

## Rebuilding modules

Many third-party modules are native and built as part of `npm install`. This is
problematic as it is likely that your host Node uses a different version of V8
to Electron. As such, all native modules must be rebuilt against Electron's
headers.

Install `electron-rebuild`:

```
npm install electron-rebuild --save-dev
```

Rebuild after each native package installed (requires Python 2.x):

```
./node_modules/.bin/electron_rebuild
```

## Windows

In order to be able to re-build modules using `electron-rebuild`, Python 2.x
must be installed and present in your path. The easiest way to achieve the latter
is by using the Git Bash shell.

You can then install the Windows build tools (effectively the .NET Framework SDK)
by running the following command in Powershell (standard command prompt will not
work) as an administrator:

```
npm install --global --production windows-build-tools
``
