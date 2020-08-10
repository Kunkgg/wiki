# systemctl -- Interface for systemd

## Basic usage

Show system status

    systemctl status

List running units

    systemctl list-units

List failed units

    systemctl --failed

List installed units

    systemctl list-unit-files

Show the cgroup slice, memory and parent for a PID or Unit-Name

    systemctl status <pid or name>

show enabled units

    systemctl list-unit-files --state=enabled

## Units

A unit can be, for example:

: service(.service)
: mount(.mount)
: device(.device)
: socket(.socket)

Some unit names contain an `@` sign (e.g. name@string.service):
this means that they are instances of a template unit.

Check units which are offer by package:

    pacman -Qql package | grep -Fe .service -e .socket -e .mount -e .device

Manage unit

: start
: stop
: restart
: reload
: status
: is-enable
: disable
: mask -- make a unite impossible to start
: unmask
: help

Reload systemd manager configuration, scanning for new or changed units

    systemctl daemon-reload

## Power management

```sh
systemctl { reboot | poweroff | suspend | hibernate | hybrid-sleep }
```

## Target

Systemd use target to group units together via
dependencies and as standardized synchronization points.
They serve a similar purpose as runlevels but act a little different.
