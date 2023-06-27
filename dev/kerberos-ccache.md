# Kerberos Credentials Cache

## Minimum CCache File Size

See https://web.mit.edu/kerberos/krb5-devel/doc/formats/ccache_file_format.html

version indicator:
- byte 0: "5"
- byte 1: version
- total: 2 bytes

header only in version 4, so skip it for now

default principal:
- name type: not in version 1, so skip it
- count of components: 4 bytes
- realm:
  - length: 4 bytes
  - value: none
- componentes: none
- total: 8 bytes

credentials, assume at least one:
- client: 8 bytes (see principal)
- server: 8 bytes (see principal)
- keyblock: 2 + 4 = 6 bytes
- authtime: 4 bytes
- starttime: 4 bytes
- endtime: 4 bytes
- renew till: 4 bytes
- is skey: 1 byte
- ticket flags: 4 bytes
- addresses: 4 bytes
- authdata: 4 bytes
- ticket: 4 bytes
- 2nd ticket: 4 bytes
- total: 59 bytes

total minimum:
2 + 8 + 59 = 69
