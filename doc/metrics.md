# HP Proliant Microserver Gen8

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
