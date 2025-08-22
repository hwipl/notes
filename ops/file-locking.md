# File Locking

Make sure only one process is performing an action at the same time with file
locking using `flock`:

```console
# terminal 1
$ flock -n sleep.lock sleep 30
# terminal 2
$ flock -n sleep.lock echo 1
# terminal 2, after sleep terminated
$ flock -n sleep.lock echo 1
1
```
