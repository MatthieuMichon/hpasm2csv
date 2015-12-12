# Parsing `hpasmcli` Output #

# Invokation

The `hpasmcli` utility can be invoked in script mode using the `-s` switch followed by the command inclosed in quotes:

```shell
$ sudo hpasmcli -s "<commands>"
```

# Temperature Output

```shell
$ sudo hpasmcli -s "show temp"

Sensor   Location              Temp       Threshold
------   --------              ----       ---------
#1        AMBIENT              19C/66F    42C/107F 
#2        PROCESSOR_ZONE       40C/104F   70C/158F 
#3        MEMORY_BD            27C/80F    87C/188F 
#4        SYSTEM_BD             -         60C/140F 
#5        SYSTEM_BD            56C/132F   105C/221F
#6        SYSTEM_BD            41C/105F   68C/154F 
#7        SYSTEM_BD            42C/107F   88C/190F 
#8        SYSTEM_BD             -         65C/149F 
#9        SYSTEM_BD            40C/104F   72C/161F 
#10       I/O_ZONE              -         100C/212F
#11       I/O_ZONE             36C/96F    64C/147F 
#12       CHASSIS_ZONE         38C/100F   68C/154F 
#13       SYSTEM_BD             -         100C/212F
```

Altough this command supports readout for 14 sensors, only nine are installed. This requires an extra filtering step.

# Shell Script

The script must perform the following actions:
* Call `hpasmcli` with the command
* Capturing the result
* Remove all unused lines
* Remove unused columns
* Convert to decimal values
* Add a comma separator
* Prepend the epoch time
* Append to a given CSV file

## Simple Versions

Calls `hpasmcli` save and saves the results without any formating:
```shell
#!/bin/sh

# Caution: Security Risk
#
# This script may be executed by cron with root privileges. As such the
# content of this script and any binaries or scripts called must be trusted.

SHOW_TEMP="show temp"

TEMPS="$(/sbin/hpasmcli -s "$SHOW_TEMP")"
echo "$TEMPS" > latest_temps.log
```
