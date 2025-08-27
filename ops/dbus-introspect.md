# D-Bus Introspection

Example from https://www.freedesktop.org/wiki/Software/systemd/dbus/:

```console
$ gdbus introspect --system --dest org.freedesktop.systemd1 --object-path /org/freedesktop/systemd1
```

https://sheitsandgiggles.com/2019/07/16/a-trip-into-dbus-send/

```console
$ dbus-send --system --print-reply --dest=[service] [objectname] [interface].[method] [parameters]dbus-send --system --print-reply --dest=org.freedesktop.systemd1 /org/freedesktop/systemd1   org.freedesktop.DBus.Introspectable.Introspect
```
