# fix-ubuntu-kworker-cpu-issue

from https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1491467

The bug can be identified by repeatedly running
cat /sys/firmware/acpi/interrupts/gpe13
where a rapidly increasing count will be seen.

Workaround:
```
sudo sh -c 'echo "disable" > /sys/firmware/acpi/interrupts/gpe13'
```
disables it until reboot
Using
```
sudo crontab -e
```
and adding the line
```
@reboot echo "disable" > /sys/firmware/acpi/interrupts/gpe13
```

works around for subsequent boots.

