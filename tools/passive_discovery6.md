# passive_discovery6

Notes
-------

Help Text
-------
```
passive_discovery6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

Syntax: passive_discovery6 [-Ds] [-m maxhop] [-R prefix] interface [script]

Options:
 -D          do also dump destination addresses (does not work with -m)
 -s          do only print the addresses, no other output
 -m maxhop   the maximum number of hops a target which is dumped may be away.
             0 means local only, the maximum amount to make sense is usually 5
 -R prefix   exchange the defined prefix with the link local prefix

Passivly sniffs the network and dump all client's IPv6 addresses detected.
Note that in a switched environment you get better results when additionally
starting parasite6, however this will impact the network.
If a script name is specified after the interface, it is called with the
detected ipv6 address as first and the interface as second option.
```

Example Usage
-------

Links
-------
