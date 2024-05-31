# Restic Backup

init repo locally:

```console
$ restic -r /data/restic-repo init
```

access repo locally, i.e., get snapshots:

```console
$ restic -r /data/restic-repo snapshots
```

backup to the repo via sftp and tag snapshot:

```console
$ restic -r sftp:10.0.0.1:/data/restic-repo --verbose backup --tag home --tag unscheduled /home/user/
```

add tags to existing snapshot:

```console
$ restic -r /data/restic-repo tag --add home,scheduled abcdef0123
```
