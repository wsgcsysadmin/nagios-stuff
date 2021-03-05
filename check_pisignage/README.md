# check_pisignage
A Nagios plugin for checking the status of [PISignage](https://www.pisignage.com/) devices.

```
$ ./check_pisignage  -h
usage: check_pisignage [-h] -u USER -p PASSWORD -d DEVICE [-t UPTIME]
                       [-k DISK_SPACE] [-f TEMPERATURE]
                       [-l {warning,info,debug}] [-s SESSION_TOKEN]

Nagios plugin to check PiSignage.com device status

optional arguments:
  -h, --help            show this help message and exit

Authentication:
  -u USER, --user USER  User name for PiSignage account
  -p PASSWORD, --password PASSWORD
                        Password for PiSignage account

Player device options:
  -d DEVICE, --device DEVICE
                        Name of device to check

Device check options:
  -t UPTIME, --uptime UPTIME
                        Uptime thresholds. In minutes. W:C
  -k DISK_SPACE, --disk-space DISK_SPACE
                        Disk space thresholds. In gigabytes. W:C
  -f TEMPERATURE, --temperature TEMPERATURE
                        Temperature thresholds. In Celsius. W:C

Logging:
  -l {warning,info,debug}, --log-level {warning,info,debug}
                        Verbosity of logging

Misc hackery:
  -s SESSION_TOKEN, --session-token SESSION_TOKEN
                        Session token to use

```

Example:
```
$ ./check_pisignage -u myuser -p supaseekret -d deli-menu-sign -f 40:50 ; echo $?
WARNING Device temperature is high: 50C.
1
```

The defaults for the thresholds are as follows:
* Up-time: warning=1m, critical=5m
* Disk space: used warning=85%, critical=90%
* Temperature: warning=70C, critical=85C
