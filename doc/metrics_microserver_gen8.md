# HP Proliant Microserver Gen8

## Available Metrics

```
hpasmcli> HELP SHOW
USAGE: SHOW [ ASR | BOOT | DIMM | F1 | FANS | HT | IML | IPL | NAME | PORTMAP | POWERSUPPLY | PXE | SERIAL | SERVER | TEMP | UID | WOL | TPM ]
```

|Item|Description|Microserver Gen8|Health Metric|
|----|-----------|----------------|--------|
|ASR|Shows the state of the ASR timer|Present|No|
|BOOT|Shows boot devices|Present|No|
|DIMM|Shows info on DIMM sockets|Present|No|
|F1|Shows the POST F1 status|Present|No|
|FANS|Shows info on installed fans|Present|**Yes**|
|HT|Shows state of processor hyperthreading|N/A|No|
|IML|Shows the IML log|Present|No|
|IPL|Shows the current device boot order|Present|No|
|NAME|Shows the server name|Present|No|
|PORTMAP|Shows NIC port Mapping information|N/A|No|
|POWERMETER|Shows info on powermeters|N/A|No|
|POWERSUPPLY|Shows info on powersupplies|Present|**Yes**|
|PXE|Shows the PXE state|Present|No|
|SERIAL|Shows the BIOS serial port status|Present|No|
|SERVER|Shows server information|Present|No|
|TEMP|Shows current temperature readings|Present|**Yes**|
|TPM|Shows state of the Trusted Platform Module|N/A|No|
|UID|Shows the UID state|Present|No|
|WOL|Shows the Wake-On-Lan status|Present|No|

## Sample Outputs

Fans:
```
hpasmcli> show fans
Fan  Location        Present Speed  of max  Redundant  Partner  Hot-pluggable
---  --------        ------- -----  ------  ---------  -------  -------------
#1   SYSTEM          Yes     NORMAL  9%      N/A        N/A      No            
```

Power-supply:
```
hpasmcli> show powersupply
Power supply #1
	Present  : Yes
	Redundant: No
	Condition: Ok
	Hotplug  : Not supported
```

Temperatures:
```
hpasmcli> show temp
Sensor   Location              Temp       Threshold
------   --------              ----       ---------
#1        AMBIENT              19C/66F    42C/107F 
#2        PROCESSOR_ZONE       40C/104F   70C/158F 
#3        MEMORY_BD            26C/78F    87C/188F 
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

Script Mode:
```
$ sudo hpasmcli -s 'show fans; show powersupply; show temp'

Fan  Location        Present Speed  of max  Redundant  Partner  Hot-pluggable
---  --------        ------- -----  ------  ---------  -------  -------------
#1   SYSTEM          Yes     NORMAL  9%      N/A        N/A      No            


Power supply #1
	Present  : Yes
	Redundant: No
	Condition: Ok
	Hotplug  : Not supported

Sensor   Location              Temp       Threshold
------   --------              ----       ---------
#1        AMBIENT              19C/66F    42C/107F 
#2        PROCESSOR_ZONE       40C/104F   70C/158F 
#3        MEMORY_BD            26C/78F    87C/188F 
#4        SYSTEM_BD             -         60C/140F 
#5        SYSTEM_BD            56C/132F   105C/221F
#6        SYSTEM_BD            41C/105F   68C/154F 
#7        SYSTEM_BD            42C/107F   88C/190F 
#8        SYSTEM_BD             -         65C/149F 
#9        SYSTEM_BD            40C/104F   72C/161F 
#10       I/O_ZONE              -         100C/212F
#11       I/O_ZONE             35C/95F    64C/147F 
#12       CHASSIS_ZONE         38C/100F   68C/154F 
#13       SYSTEM_BD             -         100C/212F
```
