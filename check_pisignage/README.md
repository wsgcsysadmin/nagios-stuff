# check_pisignage
A Nagios plugin for checking the status of [PISignage](https://www.pisignage.com/) devices.

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
