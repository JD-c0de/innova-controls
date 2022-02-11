# innova-controls

All commands are sent to the unit itself through http at its network IP address: http://[IP_ADDRESS]/api/v/1.

We just need to append the following commands and parameters where needed.

Ex: ```curl http://192.168.1.155/api/v/1/status```

It is highly recommended to set the IP of your unit to a static DHCP address.

|Action|HTTP Verb|API Endpoint|Data Needed|Extra Info|
|---|---|---|---|---|
|Status|GET|/status||Returns json object|
|Power ON|POST|/power/on|||
|Power OFF|POST|/power/off|||
|Set point|POST|/set/setpoint|p_temp=24||
|Rotation ON|POST|/set/feature/rotation|value=0||
|Rotation OFF|POST|/set/feature/rotation|value=7||
|Fan Speed|POST|/set/fan|value=[0-4]|0=auto,1=low,2=med,3=high,4=high++|
|Dehumidification|POST|/set/mode/dehumidification|||
|Fan Only|POST|/set/mode/fanonly|||
|Cooling|POST|/set/mode/cooling|||
|Heating|POST|/set/mode/heating|||
|Auto|POST|/set/mode/auto|||


JSON returned by status endpoint:
```json
{
    "RESULT": {
        "a": [],
        "cci": 0,
        "ccv": 0,
        "cfg_lastWorkingMode": 4,
        "cloudConfig": 1,
        "cloudStatus": 4,
        "cm": 0,
        "connectionStatus": 2,
        "coolingDisabled": 0,
        "cp": 0,
        "daynumber": 0,
        "fr": 7,                       <--- Fan Rotation: 0=on 7=off
        "fs": 0,                       <--- Fan Speed: 0=auto, 1=low, 2=med, 3=high, 4=high++
        "heap": 11760,
        "heatingDisabled": 1,
        "heatingResistance": 0,
        "hotelMode": 0,
        "inputFlags": 0,
        "kl": 0,
        "lastRefresh": 3956,
        "ncc": 0,
        "nm": 0,
        "ns": 0,
        "ps": 0,                        <--- Power: 0=off, 1=on
        "pwd": "************",
        "sp": 26,                       <--- Temperature Set point
        "t": 16,                        <--- Ambient Temperature
        "timerStatus": 0,
        "uptime": 159660,
        "uscm": 0,
        "wm": 4                         <--- Mode: 1=cooling, 2=heating, 3=dehumidification, 4=fanonly. 5=auto
    },
    "UID": "[MAC ADDRESS]",
    "deviceType": "001",
    "net": {
        "dhcp": "1",
        "gw": "XXX.XXX.XXX.XXX",
        "ip": "XXX.XXX.XXX.XXX",
        "sub": "255.255.255.0"
    },
    "setup": {
        "name": "Device Name",
        "serial": "YYYYYYYYY"
    },
    "success": true,
    "sw": {
        "V": "1.0.42"
    },
    "time": {
        "d": 5,
        "h": 17,
        "i": 40,
        "m": 2,
        "y": 2022
    }
}

```
