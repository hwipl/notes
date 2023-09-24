# Bind 9

Forwarding resolver configuration example:

```
// access control list "good clients"
acl goodclients {
        localhost;
        localnets;
        10.20.0.0/16;
};

options {
        // set working directory of bind
        directory "/var/cache/bind";

        // allow recursion (default: yes)
        recursion yes;

        // keep negative answers for 1 second only (default: 10800/3 hours)
        max-ncache-ttl 1;

        // enable dnssec validation and use default trust anchor (default: auto)
        dnssec-validation auto;

        // do not provide authoritative "domain does not exist" answers (default: no)
        auth-nxdomain no;

        // listen addresses
        listen-on {
                127.0.0.1;
                10.20.1.1; // Node 1 in Site 1
                // 10.20.2.1; // Node 1 in Site 2
        };
        listen-on-v6 {
                ::1;
        };

        // forwarders
        forwarders {
                10.1.1.1;
                10.2.2.2;
        };
        // only query the forwarders (default: first)
        forward only;

        // access control with acl "good clients"
        allow-query { goodclients; };
};
```

- [acl](https://bind9.readthedocs.io/en/latest/reference.html#namedconf-statement-acl)
- [directory](https://bind9.readthedocs.io/en/latest/reference.html#namedconf-statement-directory)
- [recursion](https://bind9.readthedocs.io/en/latest/reference.html#namedconf-statement-recursion)
- [max-ncache-ttl](https://bind9.readthedocs.io/en/latest/reference.html#namedconf-statement-max-ncache-ttl)
- [dnssec-validation](https://bind9.readthedocs.io/en/latest/reference.html#namedconf-statement-dnssec-validation)
- [auth-nxdomain](https://bind9.readthedocs.io/en/latest/reference.html#namedconf-statement-auth-nxdomain)
- [listen-on](https://bind9.readthedocs.io/en/latest/reference.html#namedconf-statement-listen-on)
- [listen-on-v6](https://bind9.readthedocs.io/en/latest/reference.html#namedconf-statement-listen-on-v6)
- [forwarders](https://bind9.readthedocs.io/en/latest/reference.html#namedconf-statement-forwarders)
- [forward](https://bind9.readthedocs.io/en/latest/reference.html#namedconf-statement-forward)
- [allow-query](https://bind9.readthedocs.io/en/latest/reference.html#namedconf-statement-allow-query)
