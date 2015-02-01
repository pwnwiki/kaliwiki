# arping

Notes
-------
Arping is a computer software tool that is used to discover hosts on a computer network. The program tests whether a given IP address is in use on the local network, and can get additional information about the device using that address.

Help Text
-------
```
ARPing 2.11, by Thomas Habets <thomas@habets.se>
usage: arping [ -0aAbdDeFpqrRuv ] [ -w <us> ] [ -S <host/ip> ]
              [ -T <host/ip ] [ -s <MAC> ] [ -t <MAC> ] [ -c <count> ]
              [ -i <interface> ] <host/ip/MAC | -B>

Options:

    -0     Use this option to ping with source IP address 0.0.0.0. Use this
           when you haven't configured your interface yet.  Note that  this
           may  get  the  MAC-ping  unanswered.   This  is  an alias for -S
           0.0.0.0.
    -a     Audiable ping.
    -A     Only count addresses matching  requested  address  (This  *WILL*
           break  most things you do. Only useful if you are arpinging many
           hosts at once. See arping-scan-net.sh for an example).
    -b     Like -0 but source broadcast source  address  (255.255.255.255).
           Note that this may get the arping unanswered since it's not nor-
           mal behavior for a host.
    -B     Use instead of host if you want to address 255.255.255.255.
    -c count
           Only send count requests.
    -d     Find duplicate replies. Exit with 1 if there are answers from
           two different MAC addresses.
    -D     Display answers as exclamation points and missing packets as dots.
    -e     Like -a but beep when there is no reply.
    -F     Don't try to be smart about the interface name.  (even  if  this
           switch is not given, -i overrides smartness)
    -h     Displays a help message and exits.
    -i interface
           Use the specified interface.
    -q     Does not display messages, except error messages.
    -r     Raw output: only the MAC/IP address is displayed for each reply.
    -R     Raw output: Like -r but shows "the other one", can  be  combined
           with -r.
    -s MAC Set source MAC address. You may need to use -p with this.
    -S IP  Like  -b and -0 but with set source address.  Note that this may
       	   get the arping unanswered if the target does not have routing to
           the  IP.  If you don't own the IP you are using, you may need to
           turn on promiscious mode on the interface (with -p).  With  this
           switch  you can find out what IP-address a host has without tak-
           ing an IP-address yourself.
    -t MAC Set target MAC address to use when pinging IP address.
    -T IP  Use -T as target address when pinging MACs that won't respond to
           a broadcast ping but perhaps to a directed broadcast.
           Example:
           To check the address of MAC-A, use knowledge of MAC-B and  IP-B.
           $ arping -S <IP-B> -s <MAC-B> -p <MAC-A>
    -p     Turn  on  promiscious  mode  on interface, use this if you don't
           "own" the MAC address you are using.
    -u     Show index=received/sent instead  of  just  index=received  when
           pinging MACs.
    -v     Verbose output. Use twice for more messages.
    -w     Time to wait between pings, in microseconds.
Report bugs to: thomas@habets.se
Arping home page: <http://www.habets.pp.se/synscan/>
Development repo: http://github.com/ThomasHabets/arping

```

Example Usage
-------
Arping `arping` using interface eth0 `-i eth0` with source AA:BB:CC:DD:EE:FF `-s AA:BB:CC:DD:EE:FF` with a count of two `-c 2` address 192.168.1.100 `192.168.1.100`
```
root@kali:~# arping -i eth0 -s AA:BB:CC:DD:EE:FF -p -c 2 192.168.1.100
ARPING 192.168.1.100
60 bytes from 11:22:33:44:55:66 (192.168.1.100): index=0 time=35.587 msec
60 bytes from 11:22:33:44:55:66 (192.168.1.100): index=1 time=68.289 msec
```

Links
-------
[arping GitHub project](https://github.com/ThomasHabets/arping)
[arping usage instructions](http://linux-ip.net/html/tools-arping.html)
