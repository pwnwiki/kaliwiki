# fping

Notes
-------

Help Text
-------
```
Usage: fping [options] [targets...]
   -a         show targets that are alive
   -A         show targets by address
   -b n       amount of ping data to send, in bytes (default 68)
   -B f       set exponential backoff factor to f
   -c n       count of pings to send to each target (default 1)
   -C n       same as -c, report results in verbose format
   -e         show elapsed time on return packets
   -f file    read list of targets from a file ( - means stdin) (only if no -g specified)
   -g         generate target list (only if no -f specified)
                (specify the start and end IP in the target list, or supply a IP netmask)
                (ex. fping -g 192.168.1.0 192.168.1.255 or fping -g 192.168.1.0/24)
   -H n       Set the IP TTL value (Time To Live hops)
   -i n       interval between sending ping packets (in millisec) (default 25)
   -l         loop sending pings forever
   -m         ping multiple interfaces on target host
   -n         show targets by name (-d is equivalent)
   -p n       interval between ping packets to one target (in millisec)
                (in looping and counting modes, default 1000)
   -q         quiet (don't show per-target/per-ping results)
   -Q n       same as -q, but show summary every n seconds
   -r n       number of retries (default 3)
   -s         print final stats
   -I if      bind to a particular interface
   -S addr    set source address
   -t n       individual target initial timeout (in millisec) (default 500)
   -T n       ignored (for compatibility with fping 2.4)
   -u         show targets that are unreachable
   -O n       set the type of service (tos) flag on the ICMP packets
   -v         show version
   targets    list of targets to check (if no -f specified)
```

Example Usage
-------

Links
-------
