# alive6

Notes
-------

Help Text
-------
```
alive6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

Syntax: alive6 [-I srcip6] [-i file] [-o file] [-DM] [-p] [-F] [-e opt] [-s port,..] [-a port,..] [-u port,..] [-W TIME] [-dlrvS] interface [unicast-or-multicast-address [remote-router]]

Shows alive addresses in the segment. If you specify a remote router, the
packets are sent with a routing header prefixed by fragmentation
Options:
  -i file    check systems from input file
  -o file    write results to output file
  -M         enumerate hardware addresses (MAC) from input addresses (slow!)
  -D         enumerate DHCP address space from input addresses
  -p         send a ping packet for alive check (default)
  -e dst,hop send an errornous packets: destination (default), hop-by-hop
  -s port,port,..  TCP-SYN packet to ports for alive check
  -a port,port,..  TCP-ACK packet to ports for alive check
  -u port,port,..  UDP packet to ports for alive check
  -d         DNS resolve alive ipv6 addresses
  -n number  how often to send each packet (default: local 1, remote 2)
  -W time    time in ms to wait after sending a packet (default: 1)
  -S         slow mode, get best router for each remote target or when proxy-NA
  -I srcip6  use the specified IPv6 address as source
  -l         use link-local address instead of global address
  -v         verbose (twice: detailed information, thrice: dumping all packets)
Target address on command line or in input file can include ranges in the form
of 2001:db8::1-fff or 2001:db8::1-2:0-ffff:0:0-ffff, etc.
Returns -1 on errors, 0 if a system was found alive or 1 if nothing was found.
```

Example Usage
-------

Links
-------
