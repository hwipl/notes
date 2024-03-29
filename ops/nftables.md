# nftables

distro docs:
* https://wiki.archlinux.org/title/nftables
* https://wiki.gentoo.org/wiki/Nftables

nftables wiki:
* https://wiki.nftables.org/wiki-nftables/index.php/Main_Page
* https://wiki.nftables.org/wiki-nftables/index.php/Quick_reference-nftables_in_10_minutes
* https://wiki.nftables.org/wiki-nftables/index.php/Simple_rule_management
* https://wiki.nftables.org/wiki-nftables/index.php/Configuring_chains
* https://wiki.nftables.org/wiki-nftables/index.php/Jumping_to_chain

nftables packet processing order, multiple chains/accepts
* https://unix.stackexchange.com/questions/607358/packet-processing-order-in-nftables
* https://stackoverflow.com/questions/64801304/how-right-to-make-second-input-chain-in-other-table-nftables

marking packets
* https://superuser.com/questions/1277697/making-routing-decisions-based-on-uid-using-nftables
* https://wiki.nftables.org/wiki-nftables/index.php/Setting_packet_metainformation
* https://wiki.nftables.org/wiki-nftables/index.php/Matching_packet_metainformation

named sets
* https://wiki.nftables.org/wiki-nftables/index.php/Sets
* example:
  * `nft add table ip filter`
  * `nft add set ip filter blackhole {type ipv4_addr\; flags timeout\;}`
  * `nft add element ip filter blackhole { 192.168.3.4 timeout 60s }`

example conf:
* /etc/nftables.conf

tracing/monitoring:
* https://wiki.nftables.org/wiki-nftables/index.php/Ruleset_debug/tracing
* https://unix.stackexchange.com/questions/614413/how-to-properly-log-and-view-nftables-activity

```console
$ # use "meta nftrace set 1" to enable tracing of a packet somewhere in a rule
$ # in an existing chain or, e.g., a new chain:
$ nft add chain filter trace_chain { type filter hook prerouting priority -301\; }
$ nft add rule filter trace_chain meta nftrace set 1
$ # or use more specific packet matching, e.g.: ip protocol tcp meta nftrace set 1
$ nft monitor trace
```
