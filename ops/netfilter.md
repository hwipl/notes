# Netfilter

## Packet Processing Order

- https://unix.stackexchange.com/questions/607358/packet-processing-order-in-nftables
- Diagrams: https://gist.github.com/nerdalert/a1687ae4da1cc44a437d

Diagram from source: http://www.plouf.fr.eu.org/bazar/netfilter/schema_netfilter.txt

```
Cheminement des paquets IPv4 dans Netfilter/iptables du noyau Linux 2.4
IPv4 packets path through the Linux 2.4 kernel Netfilter/iptables

                interface d'entr�e (input interface)
                                 |
                                 v
                         /-------+-------\
                         | sanity checks |
                         \-------+-------/
                                 |
                                 v hook NF_IP_PRE_ROUTING
                          +------+------+
                          | conntrack   |
                          | defrag.     |
                          +-------------+
                          | mangle      |
                          | PREROUTING  |
                          +-------------+
                          | nat (dst)   |
                          | PREROUTING  |
                          +------+------+
                                 |
                                 v
            local delivery  /----+----\    forward
           +---------------+   route   +---------------+
           |                \---------/                |
           v                                           v
     /-----+-----\                               /-----+-----\
     |  defrag.  |                               | TTL check |
     \-----+-----/                               | dec. TTL  |
           |                                     \-----+-----/
           v hook NF_IP_LOCAL_IN                       |
    +------+------+                                    |
    | mangle  (1) |                                    |
    | INPUT       |                                    |
    +-------------+                                    |
    | filter      |                                    v
    | INPUT       |                              /-----+-----\
    +-------------+                              | DF check  |
    | nat (src)(2)|                              \-----+-----/
    +-------------+                                    |
    | conntrack   |                                    |
    | confirm     |                                    | hook
    +------+------+                                    v NF_IP_FORWARD
           |                                    +------+------+
           v                                    | mangle  (1) |
   /-------+-------\                            | FORWARD     |
   | local process |                            +-------------|
   \-------+-------/                            | filter      |
           |                                    | FORWARD     |
           v                                    +------+------+
     /-----+-----\                                     |
     |   route   |                                     |
     |   frag.   |                                     |
     \-----+-----/                                     |
           |                                           |
           v hook NF_IP_LOCAL_OUT                      |
    +------+------+                                    |
    | conntrack   |                                    |
    | defrag.     |                                    |
    +-------------+                                    |
    | mangle      |                                    |
    | OUTPUT      |                                    |
    +-------------+                                    v
    | nat (dst)(3)|                              /-----+-----\
    | OUTPUT      |                              |   frag.   |
    +-------------+                              \-----+-----/
    | filter      |                                    |
    | OUTPUT      |                                    |
    +------+------+                                    |
           |                                           |
           v                                           |
     /-----+-----\                                     |
     |  reroute  |                                     |
     \-----+-----/                                     |
           |                                           |
           +------------------+     +------------------+
                              |     |
                              v     v hook NF_IP_POST_ROUTING
                          +---+-----+---+
                          | mangle  (1) |
                          | POSTROUTING |
                          +-------------+
                          | nat (src)   |
                          | defrag.     |
                          | POSTROUTING |
                          +-------------+
                          | conntrack   |
                          | confirm     |
                          | frag.       |
                          +------+------+
                                 |
                                 v
               interface de sortie (output interface)

_________________________________________________________________
Abr�viations/abbreviations :
conntrack = connection tracking
dec = decrementation
defrag = packet defragmentation/reassembly
DF = "Don't Fragment" flag in IP header
dst = destination address/port
frag = packet fragmentation
nat = network address translation
src = source address/port
TTL = "Time To Live" field in IP header
_________________________________________________________________
Notes :
(1) si/if >= 2.4.18
(2) si/if >= 2.4.29 ou/or CONFIG_IP_NF_NAT_LOCAL=y
(3) si/if < 2.4.19 ou/or >= 2.4.29 ou/or CONFIG_IP_NF_NAT_LOCAL=y
_________________________________________________________________

Derni�re mise � jour/last updated : 13/01/2006
Auteur/author : pascal.mail@plouf.fr.eu.org
Tous commentaires, corrections ou suggestions bienvenus.
Any comments, corrections or suggestions welcome.
```
