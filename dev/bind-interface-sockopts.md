# Bind Interface Socket Options

Bind to device socket option:
- `SO_BINDTODEVICE`
- https://man7.org/linux/man-pages/man7/socket.7.html

Multicast interface socket options:
- `IP_MULTICAST_IF`
- `IPV6_MULTICAST_IF`

Unicast interface socket options:
- `IP_UNICAST_IF`
- `IPV6_UNICAST_IF`
- IPv4 fixed in linux 5.19+, IPv6 maybe in 6.2+?
  - https://lore.kernel.org/all/20220829111554.GA1771@debian/T/
  - https://lore.kernel.org/netdev/7b510e87-3a34-d9c8-a9e9-65c1d93ad645@kernel.org/T/

`SO_BINDTODEVICE` and `IP_UNICAST_IF` description:
- https://github.com/systemd/systemd/issues/11935#issuecomment-618691018
  - might be outdated due to fixes in the linux kernel in newer kernels, see
    patches in other links above
