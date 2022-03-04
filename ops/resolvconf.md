# resolvconf

man page
* man 8 resolvconf

description of resolvconf and exclusive dns, `~.` and `default-route`:
* https://github.com/systemd/systemd/issues/17529
* https://github.com/systemd/systemd/issues/17529#issuecomment-730522444
* https://github.com/systemd/systemd/pull/17678

split dns
* https://fedoraproject.org/wiki/Changes/systemd-resolved#Split_DNS

dns server in netns
* https://serverfault.com/questions/614574/how-to-set-dns-exclusively-for-a-network-namespace-in-linux

`resolvconf` can be a link to `resolvectl`, that supports `resolvconf`
compatible execution.

## resolvectl

Setting exclusive DNS, `resolvectl` version of `resolvconf -a $DEVICE -m 0 -x`:

```console
$ sudo resolvectl dns $DEVICE $SERVER
$ sudo resolvectl domain $DEVICE $SEARCH_DOMAINS ~.
$ sudo resolvectl default-route $DEVICE yes
```

Reverting changes, `resolvectl` version of `resolvconf -d $DEVICE -f`:

```console
$ sudo resolvectl revert $DEVICE
```

Flushing caches

```console
$ sudo resolvectl flush-caches
```
