# xprobe2

Notes
-------

Help Text
-------
```
Xprobe2 v.0.3 Copyright (c) 2002-2005 fyodor@o0o.nu, ofir@sys-security.com, meder@o0o.nu

usage: xprobe2 [options] target
Options:
          -v                       Be verbose
          -r                       Show route to target(traceroute)
          -p <proto:portnum:state> Specify portnumber, protocol and state.
                                   Example: tcp:23:open, UDP:53:CLOSED
          -c <configfile>          Specify config file to use.
          -h                       Print this help.
          -o <fname>               Use logfile to log everything.
          -t <time_sec>            Set initial receive timeout or roundtrip time.
          -s <send_delay>          Set packsending delay (milseconds).
          -d <debuglv>             Specify debugging level.
          -D <modnum>              Disable module number <modnum>.
          -M <modnum>              Enable module number <modnum>.
          -L                       Display modules.
          -m <numofmatches>        Specify number of matches to print.
          -T <portspec>            Enable TCP portscan for specified port(s).
                                   Example: -T21-23,53,110
          -U <portspec>            Enable UDP portscan for specified port(s).
          -f                       force fixed round-trip time (-t opt).
          -F                       Generate signature (use -o to save to a file).
          -X                       Generate XML output and save it to logfile specified with -o.
          -B                       Options forces TCP handshake module to try to guess open TCP port
          -A                       Perform analysis of sample packets gathered during portscan in
                                   order to detect suspicious traffic (i.e. transparent proxies,
                                   firewalls/NIDSs resetting connections). Use with -T.
```

Example Usage
-------

Links
-------
