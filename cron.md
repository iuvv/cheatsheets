---
title: Cron
category: CLI
layout: 2017/sheet
updated: 2017-08-26
weight: -3
---

## Format
{: .-two-column}

### Format

```
Min  Hour Day  Mon  Weekday
```
{: .-setup}

```
*    *    *    *    *  command to be executed
```

```
┬    ┬    ┬    ┬    ┬
│    │    │    │    └─  Weekday  (0=Sun .. 6=Sat)
│    │    │    └──────  Month    (1..12)
│    │    └───────────  Day      (1..31)
│    └────────────────  Hour     (0..23)
└─────────────────────  Minute   (0..59)
```
{: .-setup.-box-chars}

### Examples

| Example        | Description           |
| ---            | ---                   |
| `0 * * * *`    | every hour            |
| `*/15 * * * *` | every 15 mins         |
| `0 */2 * * *`  | every 2 hours         |
| `0 0 0 * 0`    | every Sunday midnight |
| ---            | ---                   |
| `@reboot`      | every reboot          |

### Example2

```bash
$ crontab -l
#SHELL=/usr/bin/bash
#PATH=/usr/local/bin:/usr/bin

#m      h       dom     mon     dow     user command
0	2	*	*	*	sudo yum update -y >>/home/tom/log/crontab/update.log
30	22	*	*	1-5	cd /home/jlch/registry/tramitter_client && node ./index.js >> index.js.log 2>&1
```

### Crontab

```bash
# Adding tasks easily
echo "@reboot echo hi" | crontab
```

```bash
# Open in editor
crontab -e
```

```bash
# List tasks
crontab -l [-u user]
```
