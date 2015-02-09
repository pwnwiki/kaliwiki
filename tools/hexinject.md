# hexinject

Notes
-------
HexInject is a very versatile packet injector and sniffer, that provide a command-line framework for raw network access.
It's designed to work together with others command-line utilities, and for this reason it facilitates the creation of powerful shell scripts capable of reading, intercepting and modifying network traffic in a transparent manner.


Help Text
-------
```
xInject 1.5 [hexadecimal packet injector/sniffer]
written by: Emanuele Acri <crossbower@gmail.com>

Usage:
   hexinject <mode> <options>

Options:
  -s sniff mode
  -p inject mode
  -r raw mode (instead of the default hexadecimal mode)
  -f <filter> custom pcap filter
  -i <device> network device to use
  -F <file> pcap file to use as device (sniff mode only)
  -c <count> number of packets to capture
  -t <time> sleep time in microseconds (default 100)
  -I list all available network devices

Injection options:
  -C disable automatic packet checksum
  -S disable automatic packet size
  
Interface options:
  -P disable promiscuous mode
  -M put the wireless interface in monitor mode
     (experimental: use airmon-ng instead...)

Other options:
  -h help screen

```

Example Usage
-------


```
hexinject -s -i eth0
```

Links
-------
[Hexinject Sourceforge project](http://hexinject.sourceforge.net/
