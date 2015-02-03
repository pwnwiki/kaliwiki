# Braa

Notes
-------

Help Text
-------
```
braa 0.81 - Mateusz 'mteg' Golicz <mtg@elsat.net.pl>, 2003 - 2006
usage: braa [options] [query1] [query2] ...
  -h        Show this help.
  -2        Claim to be a SNMP2C agent.
  -v        Show short summary after doing all queries.
  -x        Hexdump octet-strings
  -t <s>    Wait <s> seconds for responses.
  -d <s>    Wait <s> microseconds after sending each packet.
  -p <s>    Wait <s> miliseconds between subsequent passes.
  -f <file> Load queries from file <file> (one by line).
  -a <time> Quit after <time> seconds, independent on what happens.
  -r <rc>   Retry count (default: 3).

Query format:
  GET:   [community@]iprange[:port]:oid[/id]
  WALK:  [community@]iprange[:port]:oid.*[/id]
  SET:   [community@]iprange[:port]:oid=value[/id]

Examples:
         public@10.253.101.1:161:.1.3.6.*
         10.253.101.1-10.253.101.255:.1.3.6.1.2.1.1.4.0=sme
         10.253.101.1:.1.3.6.1.2.1.1.1.0/description

It is also possible to specify multiple queries at once:
         10.253.101.1-10.253.101.255:.1.3.6.1.2.1.1.4.0=sme,.1.3.6.*
         (Will set .1.3.6.1.2.1.1.4.0 to 'me' and do a walk starting from .1.3.6)


Values for SET queries have to be prepended with a character specifying the value type:
  i      is INTEGER
  a      is IPADDRESS
  s      is OCTET STRING
  o      is OBJECT IDENTIFIER
If the type specifier is missing, the value type is auto-detected

```

Example Usage
-------

Links
-------

