# IP Link Command

```console
$ ip -details link show
```

```console
$ ip -details -j l | jq -r '.[]|"\(.ifname), \(.link_type), \(.linkinfo.info_data.type), \(.linkinfo.info_kind), \(.linkinfo.info_slave_kind)"' | column -t -s ','
```

- src: https://unix.stackexchange.com/questions/272850/how-to-determine-the-logical-type-of-a-linux-network-device
- related: https://stackoverflow.com/questions/4475420/detect-network-connection-type-in-linux
