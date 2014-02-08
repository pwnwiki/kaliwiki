# thcping6

Notes
-------

Help Text
-------
```
thcping6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

Syntax: thcping6 [-af] [-H o:s:v] [-D o:s:v] [-F dst] [-t ttl] [-c class] [-l label] [-d size] [-S port|-U port] interface src6 dst6 [srcmac [dstmac [data]]]

Craft your special icmpv6 echo request packet.
You can put an "x" into src6, srcmac and dstmac for an automatic value.
Options:
  -a              add a hop-by-hop header with router alert option.
  -q              add a hop-by-hop header with quickstart option.
  -E              send as ethertype IPv4
  -H o:s:v        add a hop-by-hop header with special content
  -D o:s:v        add a destination header with special content
  -D "xxx"        add a large destination header which fragments the packet
  -f              add a one-shot fragementation header
  -F ipv6address  use source routing to this final destination
  -t ttl          specify TTL (default: 64)
  -c class        specify a class (0-4095)
  -l label        specify a label (0-1048575)
  -d data_size    define the size of the ping data buffer
  -S port         use a TCP SYN packet on the defined port instead of ping
  -U port         use a UDP packet on the defined port instead of ping
o:s:v syntax: option-no:size:value, value is in hex, e.g. 1:2:feab
Returns -1 on error or no reply, 0 on normal reply or 1 on error reply.
```

Example Usage
-------

Links
-------
