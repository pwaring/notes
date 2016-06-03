# Obnam

Iimplement a "virtual file system" inside Obnam, see `obnamlib/vfs.py` for the
interface, and `obnamlib/plugins/sftp_plugin.py` for an example.

Parsing config: `cliapp.Settings`, the `cliapp.Application.setup` method may be
appropriate.

Obnam plugin, which can add new settings and a hook callback to do things when
configs and command line have been parsed.
