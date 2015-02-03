# tcpflow

Notes
-------

Help Text
-------
```
tcpflow version 0.21 by Jeremy Elson <jelson@circlemud.org>

usage: tcpflow [-chpsv] [-b max_bytes] [-d debug_level] [-f max_fds]
          [-i iface] [-r file] [expression]

        -b: max number of bytes per flow to save
        -c: console print only (don't create files)
        -C: console print only, but without the display of source/dest header
        -d: debug level; default is 1
        -e: output each flow in alternating colors
        -f: maximum number of file descriptors to use
        -h: print this help message
        -i: network interface on which to listen
            (type "ifconfig -a" for a list of interfaces)
        -p: don't use promiscuous mode
        -r: read packets from tcpdump output file
        -s: strip non-printable characters (change to '.')
        -v: verbose operation equivalent to -d 10
expression: tcpdump-like filtering expression

See the man page for additional information.
```

Example Usage
-------

Links
-------

