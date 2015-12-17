# hpasm2csv

Set of scripts storing system health information polled from hpasm into CSV format.

# Motivations

1. As owner of a HP Proliant Microserver Gen8 server, I'm interested in all long-term trends relevant to the health of this system.
2. Get some practical experience with `cron` and `logrotate`.
3. Look into computer security best practices since I have to deal with the `hpasmcli` utility, which requires superuser privileges.

# Requirements

## Linux

The scripts contained in this repo are tested with a Debian Jessie Linux distribution.

## hpasmcli

The `hpasmcli` utility is part of the *hp-health* package, present on the [HP Software Delivery Repository](http://downloads.linux.hp.com/SDR/project/mcp/).

# Theory of Operation

Steps:

1. The system-level crontab references a shell script which is to be run every several times per hour.
2. This shell-script (run with root privileges) calls the `hpasmcli` command-line utility and captures its output.
3. The output is filtered and relevant information is extracted and formated.
4. The newly formated data along with timestamp information is appended in CSV file.

As the CSV will grow bigger, a logrotate rule manages it size by splitting and compressing older entries.

## CSV Fields

|Epoch Time|Ambient Temp|CPU Temp|DIMM Temp|M/B Temp #1|M/B Temp #2|M/B Temp #3|M/B Temp #4|IO Zone Temp|Chassis Temp|Fan %|P/S Ok|
|---|---|---|---|---|---|---|---|---|---|---|---|

# Milestones

- [X] listing of relevant system health metrics
 
Scripting:

- [X] `hpasmcli` output in a text file
- [X] `hpasmcli` output parsed in a set of values
- [X] `hpasmcli` output parsed and appended in a CSV file

Cron:

- [X] dummy script called several times per hour
- [X] `hpasm2csv` script called

Logrotate:

- [ ] `logortate` rule for handling the CSV file

