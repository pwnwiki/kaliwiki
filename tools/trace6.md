# trace6

Notes
-------

Help Text
-------
```
trace6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

Syntax: trace6 [-abdt] [-s src6] interface targetaddress [port]

Options:
  -a       insert a hop-by-hop header with router alert option.
  -D       insert a destination extension header
  -E       insert a destination extension header with an invalid option
  -F       insert a one-shot fragmentation header
  -b       instead of an ICMP6 Ping, use TooBig (you will not see the target)
  -B       instead of an ICMP6 Ping, use PingReply (you will not see the target)
  -d       resolves the IPv6 addresses to DNS.
  -t       enables tunnel detection
  -s src6  specifies the source IPv6 address
Maximum hop reach: 31

A basic but very fast traceroute6 program.
If no port is specified, ICMP6 Ping requests are used, otherwise TCP SYN
packets to the specified port. Options D, E and F can be use multiple times.
```

Example Usage
-------

Links
-------
