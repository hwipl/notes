# ISC DHCP Server

## Static Routes

* [RFC 3442](https://www.rfc-editor.org/rfc/rfc3442)
* Sources:
  * https://unix.stackexchange.com/questions/500480/add-static-route-to-one-specific-address-to-dhcpd-conf
  * https://github.com/fishilico/generic-config/blob/master/etc-server/dhcp/dhcpd.conf
  * https://gist.github.com/teliot/e92ea7fd7f7ebd617d487c17904744be

```
option classless-routes code 121 = array of unsigned integer 8;
option classless-routes-win code 249 = array of unsigned integer 8;

option classless-routes 24, 192,168,2, 192,168,1,1, 0, 192,168,1,1;
option classless-routes-win 24, 192,168,2, 192,168,1,1, 0, 192,168,1,1;
```
