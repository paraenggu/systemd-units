# systemd-units
Collection if various systemd unit files

## eix-sync
Systemd service and timer unit for Gentoo's [eix-sync](https://github.com/vaeth/eix/):
* [<code>eix-sync.service</code>](eix-sync.service): Calls Gentoo's <code>/usr/bin/eix-sync -q</code> with a high nice level and a low IO best-effort scheduling priority.
* [<code>eix-sync.timer</code>](eix-sync.timer): Corresponding timer unit, which calls the <code>eix-sync.service</code> daily at 09:00

Usage:
Manually start eix-sync via <code>systemctl start eix-sync</code> or install the timer unit:
```bash
systemctl enable eix-sync.timer
systemctl start eix-sync.timer

systemctl list-timers eix-sync.timer
```
```
NEXT                         LEFT     LAST                         PASSED       UNIT           ACTIVATES
Mon 2017-01-16 09:00:00 CET  21h left Son 2017-01-15 10:21:52 CET  1h 35min ago eix-sync.timer eix-sync.service

1 timers listed.
```
