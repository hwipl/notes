# Overriding DNS Entries with Response Policy Zone in Bind

Sources:
- https://serverfault.com/questions/18748/overriding-some-dns-entries-in-bind-for-internal-networks
- https://www.redpill-linpro.com/techblog/2015/12/08/dns-rpz.html
- https://blog.ddavo.me/posts/tutorials/bind-override/

Add `response-policy` to /etc/bind/named.conf.options:

```
acl goodclients {
        localhost;
        localnets;
};

options {
        directory "/var/cache/bind";

        recursion yes;
        allow-query { goodclients; };

        forwarders {
                192.168.1.1;
        };
        forward only;
        max-ncache-ttl 1;

        dnssec-validation auto;

        auth-nxdomain no;
        listen-on {
                127.0.0.1;
                192.168.2.1;
        };
        listen-on-v6 {
                ::1;
        };
        response-policy { zone "rpz"; };
};
```

Add zone `rpz` to /etc/bind/named.conf.local:

```
# local network zone
zone "network.lan" {
    type master;
    file "/etc/bind/db.network.lan";
};

# local network response policy zone
zone "rpz" {
    type master;
    file "/etc/bind/db.rpz";
};
```

Add zone file /etc/bind/db.rpz:

```
$TTL    604800
@       IN      SOA     network.lan. root.network.lan. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL

@       IN      NS      ns.network.lan.
@       IN      A       192.168.2.1
@       IN      AAAA    ::1
ns      IN      A       192.168.2.1

www.example.com       IN      A       192.168.1.1
```

Restart named:

```console
$ sudo systemctl restart named.service
```
