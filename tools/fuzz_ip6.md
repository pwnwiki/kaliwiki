# fuzz_ip6

Notes
-------

Help Text
-------
```
fuzz_ip6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

Syntax: fuzz_ip6 [-x] [-t number | -T number] [-p number] [-IFSDHRJ] [-X|-1|-2|-3|-4|-5|-6|-7|-8|-9|-0 port] interface unicast-or-multicast-address [address-in-data-pkt]

Fuzzes an icmp6 packet
Options:
 -X         do not add any ICMP/TCP header (tranport laye)
 -1         fuzz ICMP6 echo request (default)
 -2         fuzz ICMP6 neighbor solicitation
 -3         fuzz ICMP6 neighbor advertisement
 -4         fuzz ICMP6 router advertisement
 -5         fuzz multicast listener report packet
 -6         fuzz multicast listener done packet
 -7         fuzz multicast listener query packet
 -8         fuzz multicast listener v2 report packet
 -9         fuzz multicast listener v2 query packet
 -0         fuzz node query packet
 -s port    fuzz TCP-SYN packet against port
 -x         tries all 256 values for flag and byte types
 -t number  continue from test no. number
 -T number  only performs test no. number
 -p number  perform an alive check every number of tests (default: none)
 -a         do not perform initial and final alive test
 -n number  how many times to send each packet (default: 1)
 -I         fuzz the IP header too
 -F         add one-shot fragmentation, and fuzz it too (for 1)
 -S         add source-routing, and fuzz it too (for 1)
 -D         add destination header, and fuzz it too (for 1)
 -H         add hop-by-hop header, and fuzz it too (for 1 and 5-9)
 -R         add router alert header, and fuzz it too (for 5-9 and all)
 -J         add jumbo packet header, and fuzz it too (for 1)
You can only define one of -0 ... -9 and -s, defaults to -1.
Returns -1 on error, 0 on tests done and targt alive or 1 on target crash.
```

Example Usage
-------

Links
-------

