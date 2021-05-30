# CobaltStrikeParser
Forked from https://github.com/Sentinel-One/CobaltStrikeParser

Python parser for CobaltStrike Beacon's configuration, supports limited byte swapping to decode the configuration. 

## Description
Use `parse_beacon_config.py` for stageless beacons, memory dumps or C2 urls with metasploit compatibility mode (default true).  
Many stageless beacons are PEs where the beacon code itself is stored in the `.data` section and xored with 4-byte key.  
The script tries to find the xor key and data heuristically, decrypt the data and parse the configuration from it.

This is designed, so it can be used as a library too.

The repo now also includes a small communication module (comm.py) that can help with communicating to a C2 server as a beacon.  

## Usage
```
usage: parse_beacon_config.py [-h] [--json] [--quiet] [--version VERSION] [--byteswap] beacon

Parses CobaltStrike Beacon's configuration from PE, memory dump or URL.

positional arguments:
  beacon             This can be a file path or a url (if started with http/s)

optional arguments:
  -h, --help         show this help message and exit
  --json             Print as json
  --quiet            Do not print missing or empty settings
  --version VERSION  Try as specific cobalt version (3 or 4). If not specified, tries both.
  --byteswap         Try a byteswap if decoding doesn't make sense
```

## Extra
To use the communication poc copy it to the main folder and run it from there.
For installing the M2Crypto library (a requirement for the poc) on Windows, it's easiest with installers found online, and not through pip.