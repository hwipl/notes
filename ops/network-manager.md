# Network Manager

NetworkManager info:
* https://wiki.archlinux.org/title/NetworkManager

SecretAgent:
* https://developer-old.gnome.org/NetworkManager/stable/gdbus-org.freedesktop.NetworkManager.SecretAgent.html
* https://manpages.debian.org/testing/network-manager/nmcli.1.en.html#SECRET_AGENT
* https://api.kde.org/frameworks/networkmanager-qt/html/classNetworkManager_1_1SecretAgent.html

Python module info and description of SecretAgent interaction:
* https://pythonhosted.org/python-networkmanager/#NetworkManager.SecretAgent

NetworkManager + wpa_supplicant debugging:
* https://www.programmerall.com/article/1527177960/

## Examples

### Auto-Configuration Connection

Adding a configuration with auto-configuration of IP addresses etc:

```
$ nmcli connection add type ethernet con-name Default ifname eth0
```

### Auto-Connect Priorities

Specifying autoconnect (auto connect is enabled by default) priorities for
connections:

```
$ nmcli connection add type ethernet con-name Default ifname eth0 \
        connection.autoconnect-priority -999
```

https://developer-old.gnome.org/NetworkManager/stable/settings-connection.html:

"The autoconnect priority. If the connection is set to autoconnect, connections
with higher priority will be preferred. Defaults to 0. The higher number means
higher priority."

### Connection for all Network Interfaces

Adding connection for all compatible devices (from
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/networking_guide/sec-configuring_ip_networking_with_nmcli#sec-Locking_a_Profile_to_a_Specific_Device_Using_nmcli):

```console
$ nmcli connection add type ethernet con-name connection-name ifname "*"
```

"Note that you have to use the ifname argument even if you do not want to set a
specific interface. Use the wildcard character * to specify that the profile
can be used with any compatible device."
