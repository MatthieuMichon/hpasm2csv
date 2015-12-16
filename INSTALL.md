Create a `/var/log/hpasm2csv` directory:

```
$ sudo mkdir /var/log/hpasm2csv
```

Move the `hpasm2csv` script from this repo in `/usr/bin`, check that this file is owned by *root* and cannot be modified by anybody else.
```
$ sudo cp hpasm2csv /usr/bin
$ ls -l /usr/bin/hpasm2csv
-rwxr--r-- 1 root root 1452 Dec 16 01:16 /usr/bin/hpasm2csv
```
