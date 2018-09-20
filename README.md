# UptimeRobot Monitor Utility
A bash script to work with [UptimeRobot](https://uptimerobot.com) monitors via the API. It checks to make sure that the API key that you provided is valid before performing any requested operations.

It is recommened that you install the JQ package to automatically format the JSON output into a much more human-readable and colorized output.

## Setting it up

To get the script working you will need to download it onto your preferred machine:

```bash
tronyx@suladan:~# wget https://raw.githubusercontent.com/christronyxyocum/uptimerobot-monitor-utility/master/uptimerobot_monitor_utility.sh
--2018-09-20 17:32:58--  https://raw.githubusercontent.com/christronyxyocum/uptimerobot-monitor-utility/master/uptimerobot_monitor_utility.sh
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.20.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.20.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8339 (8.1K) [text/plain]
Saving to: ‘uptimerobot_monitor_utility.sh’

uptimerobot_monitor_utility.sh                              100%[========================================================================================================================================>]   8.14K  --.-KB/s    in 0s

2018-09-20 17:32:58 (39.2 MB/s) - ‘uptimerobot_monitor_utility.sh’ saved [8339/8339]
```

Then make it executable:

```bash
tronyx@suladan:~# chmod a+x uptimerobot_monitor_utility.sh
```

Finally, open the script with your favorite text editor and add your UptimeRobot API key.

## Usage

```bash
tronyx@suladan:~# ./uptimerobot_monitor_utility.sh
    Usage: uptimerobot_monitor_utility.sh -[OPTION] (ARGUMENT)...

    -l          List all UptimeRobot monitors.
    -f          Find all paused UptimeRobot monitors.
    -n          Find all paused UptimeRobot monitors
                without an unpause prompt.
    -p VALUE    Pause specified UptimeRobot monitors.
                Option accepts arguments in the form of "all"
                or a comma-separated list of monitors, IE:
                "uptimerobot_monitor_utility.sh -p all"
                "uptimerobot_monitor_utility.sh -p 18095687,18095688,18095689"
    -u VALUE    Unpause specified UptimeRobot monitors.
                Option accepts arguments in the form of "all"
                or a comma-separated list of monitors, IE:
                "uptimerobot_monitor_utility.sh -u all"
                "uptimerobot_monitor_utility.sh -u 18095687,18095688,18095689"
    -h          Display this usage dialog.
```

## Examples
### List all monitors

```json
tronyx@suladan:~# ./uptimerobot_monitor_utility.sh -l
The following UptimeRobot monitors were found in your UptimeRobot account:
Plex (ID: 779783111)
Radarr (ID: 780859973)
Sonarr (ID: 780859962)
Tautulli (ID: 780859975)
```

### Find paused monitors

```json
tronyx@suladan:~# ./uptimerobot_monitor_utility.sh -f
The following UptimeRobot monitors are currently paused:
Plex (ID: 779783111)
Radarr (ID: 780859973)
Sonarr (ID: 780859962)
Tautulli (ID: 780859975)
Would you like to unpause the paused monitors? ([y]es or [n]o):
```

### Pause all monitors

```json
tronyx@suladan:~# ./uptimerobot_monitor_utility.sh -p all
Pausing Plex:
{
  "stat": "ok",
  "monitor": {
    "id": 779783111
  }
}

Pausing Radarr:
{
  "stat": "ok",
  "monitor": {
    "id": 780859973
  }
}

Pausing Sonarr:
{
  "stat": "ok",
  "monitor": {
    "id": 780859962
  }
}

Pausing Tautulli:
{
  "stat": "ok",
  "monitor": {
    "id": 780859975
  }
}
```

### Pause specific monitors

```json
tronyx@suladan:~# ./uptimerobot_monitor_utility.sh -p 779783111,780859973
Pausing Plex:
{
  "stat": "ok",
  "monitor": {
    "id": 779783111
  }
}

Pausing Radarr:
{
  "stat": "ok",
  "monitor": {
    "id": 780859973
  }
}
```

### Unpause all monitors

```json
tronyx@suladan:~# ./uptimerobot_monitor_utility.sh -u all
Unpausing Plex:
{
  "stat": "ok",
  "monitor": {
    "id": 779783111
  }
}

Unpausing Radarr:
{
  "stat": "ok",
  "monitor": {
    "id": 780859973
  }
}

Unpausing Sonarr:
{
  "stat": "ok",
  "monitor": {
    "id": 780859962
  }
}

Unpausing Tautulli:
{
  "stat": "ok",
  "monitor": {
    "id": 780859975
  }
}
```

### Unpause specific monitors

```json
tronyx@suladan:~# ./uptimerobot_monitor_utility.sh -u 779783111,780859973
Unpausing Plex:
{
  "stat": "ok",
  "monitor": {
    "id": 779783111
  }
}

Unpausing Radarr:
{
  "stat": "ok",
  "monitor": {
    "id": 780859973
  }
}
```
