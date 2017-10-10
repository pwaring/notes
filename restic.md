# Restic

## Creating a repository

To create a repository at `/mnt/backups`:

`restic init --repo /mnt/backups`

You will be prompted for a password twice. This password can be stored in
`RESTIC_PASSWORD` or a file pointed to from `RESTIC_PASSWORD_FILE` or
`--password-file`.

## Backing up

To backup files, supply the repository name and the list of files:

`restic -r /mnt/backups backup ${HOME}`

After backing up, check that there are no errors:

`restic -r /mnt/backups check`
