# Log Directory

Create a `/var/log/hpasm2csv` directory:

```
$ sudo mkdir /var/log/hpasm2csv
```

# Script Location

Move the `hpasm2csv` script from this repo in `/usr/sbin`, check that this file is owned by *root* and cannot be modified by anybody else.
```
$ sudo cp hpasm2csv /usr/sbin
$ ls -l /usr/sbin/hpasm2csv
-rwxr--r-- 1 root root 1452 Dec 16 01:16 /usr/bin/hpasm2csv
```

# Root Crontab

```
$ sudo crontab -e
```

The following line must be added:
```
*/15 * * * * if [ -x /usr/sbin/hpasm2csv ]; then /usr/sbin/hpasm2csv >> /var/log/hpasm2csv/hpasm2csv.csv.log; fi
```
