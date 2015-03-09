# dnstracer

Notes
-------

Help Text
-------
```
DNSTRACER version 1.8.1 - (c) Edwin Groothuis - http://www.mavetju.org
Usage: dnstracer [options] [host]
	-c: disable local caching, default enabled
	-C: enable negative caching, default disabled
	-o: enable overview of received answers, default disabled
	-q <querytype>: query-type to use for the DNS requests, default A
	-r <retries>: amount of retries for DNS requests, default 3
	-s <server>: use this server for the initial request, default localhost
	             If . is specified, A.ROOT-SERVERS.NET will be used.
	-t <maximum timeout>: Limit time to wait per try
	-v: verbose
	-S <ip address>: use this source address.
	-4: don't query IPv6 servers
```

Example Usage
-------
####**Simple example for www.mavetju.org**

```
[~] edwin@k7>dnstracer www.mavetju.org
Tracing to www.mavetju.org via 127.0.0.1, timeout 15 seconds
127.0.0.1 (127.0.0.1)
 |\___ B.ROOT-SERVERS.NET [.] (128.9.0.107)
 |     |\___ M.GTLD-SERVERS.NET [org] (202.153.114.101)
 |     |     |\___ NS2.SECONDARY.COM [mavetju.org] (198.133.199.4) Got authoritative answer
 |     |      \___ NS1.SECONDARY.COM [mavetju.org] (198.133.199.3) Got authoritative answer
 |     |\___ E.GTLD-SERVERS.NET [org] (192.12.94.30)
 |     |     |\___ NS2.SECONDARY.COM [mavetju.org] (198.133.199.4) (cached)
 |     |      \___ NS1.SECONDARY.COM [mavetju.org] (198.133.199.3) (cached)
 |     |\___ K.GTLD-SERVERS.NET [org] (213.177.194.5)
 |     |     |\___ NS2.SECONDARY.COM [mavetju.org] (198.133.199.4) (cached)
 |     |      \___ NS1.SECONDARY.COM [mavetju.org] (198.133.199.3) (cached)
[...]
 |      \___ A.GTLD-SERVERS.NET [org] (192.5.6.30)
 |           |\___ NS2.SECONDARY.COM [mavetju.org] (198.133.199.4) (cached)
 |            \___ NS1.SECONDARY.COM [mavetju.org] (198.133.199.3) (cached)
 |\___ F.ROOT-SERVERS.NET [.] (192.5.5.241)
 |     |\___ M.GTLD-SERVERS.NET [org] (202.153.114.101) (cached)
 |     |\___ E.GTLD-SERVERS.NET [org] (192.12.94.30) (cached)
 |     |\___ K.GTLD-SERVERS.NET [org] (213.177.194.5) (cached)
 |     |\___ J.GTLD-SERVERS.NET [org] (210.132.100.101) (cached)
 |     |\___ F.GTLD-SERVERS.NET [org] (192.35.51.30) (cached)
[...]
 |      \___ A.GTLD-SERVERS.NET [org] (192.5.6.30) (cached)
 |\___ G.ROOT-SERVERS.NET [.] (192.112.36.4)
 |     |\___ M.GTLD-SERVERS.NET [org] (202.153.114.101) (cached)
[...]
```
This trace is done after a clean start of the DNS server. That means that there is no data available, except the zones the server is authoritive for and the root-servers.

This DNS server doesn't know anything about mavetju.org, so it forwards returns pointers to the root-servers. The root-servers forward us to the global-top-level-domain-servers, the ones which handle for example .com, .org, .net and the country domains.

The zone for mavetju.org is hosted by Secondary.com, and that is the one which is giving us answers. The answers are cached so we don't ask unnecessary requests.

####**Using a different server to start with**

To prevent too much information (the example above would have generated 480 lines output), we can specify a server to start with:
```
[~] edwin@k7>dnstracer -o -s m.gtld-servers.net www.mavetju.org
Tracing to www.mavetju.org via m.gtld-servers.net, timeout 15 seconds
m.gtld-servers.net (202.153.114.101) 
 |\___ NS2.SECONDARY.COM [mavetju.org] (198.133.199.4) Got authoritative answer
  \___ NS1.SECONDARY.COM [mavetju.org] (198.133.199.3) Got authoritative answer

NS1.SECONDARY.COM (198.133.199.3)       www.mavetju.org -> topaz.mavetju.org
NS1.SECONDARY.COM (198.133.199.3)       topaz.mavetju.org -> 212.204.230.141
NS2.SECONDARY.COM (198.133.199.4)       www.mavetju.org -> topaz.mavetju.org
NS2.SECONDARY.COM (198.133.199.4)       topaz.mavetju.org -> 212.204.230.141
```
The option -s specifies the server. The name of the server can be replaced by an IP address or with a dot (.) to indicate it should use A.ROOT-SERVERS.NET. The option -o displays an overview of the received answers at the end of the run.

####**PTR records**

PTR records have to be specified the same as `normal' PTR records: either with the .in-addr.arpa or the ip6.int suffix.

```
[~] edwin@k7>dnstracer -q ptr 1.0.0.127.in-addr.arpa
Tracing to 1.0.0.127.in-addr.arpa via 127.0.0.1, timeout 15 seconds
127.0.0.1 (127.0.0.1) Got authoritative answer 

127.0.0.1 (127.0.0.1)                   1.0.0.127.in-addr.arpa -> localhost.mavetju.org
```
####**SOA records**

Are used normally, but they give a somewhat longer output with the serial number, the mname and rname fields.
```
[~] edwin@k7>dnstracer -q soa -o mavetju.org
Tracing to mavetju.org via 127.0.0.1, timeout 15 seconds
127.0.0.1 (127.0.0.1) 
 |\___ ns2.mavetju.org [mavetju.org] (198.133.199.3) Got authoritative answer 
  \___ ns3.mavetju.org [mavetju.org] (198.133.199.4) Got authoritative answer 

ns3.mavetju.org (198.133.199.4)         mavetju.org -> serial: 30548 mname: ns2.mavetju.org rname: hostmaster.mavetju.org
ns2.mavetju.org (198.133.199.3)         mavetju.org -> serial: 30548 mname: ns2.mavetju.org rname: hostmaster.mavetju.org
```
####**Timeouts and broken servers**
```
[~] edwin@k7>dnstracer -q cname -s M.GTLD-SERVERS.NET fataldimensions.nl.eu.org
Tracing to fataldimensions.nl.eu.org via M.GTLD-SERVERS.NET, timeout 15 seconds
M.GTLD-SERVERS.NET (202.153.114.101) 
 |\___ AUTH1.DNS.ELM.NET [eu.org] (206.131.200.70) Got authoritative answer 
 |\___ RELAY-1.FTEL.CO.UK [eu.org] (192.65.220.24) 
 |     |\___ ns.cistron.nl [nl.eu.org] (195.64.65.25) Got authoritative answer 
 |     |\___ ns.lf.net [nl.eu.org] (212.9.160.1) Lame server 
 |     |\___ ns.eu.org [nl.eu.org] (137.194.2.218) Lame server 
 |     |\___ ns2.ispi.net [nl.eu.org] (206.131.193.15) Got answer 
 |     |\___ ns.patriots.net [nl.eu.org] (206.131.200.40) Got authoritative answer 
 |      \___ auth1.dns.elm.net [nl.eu.org] (206.131.200.70) (cached)
 |\___ NS2.GANDI.NET [eu.org] (212.73.209.247) 
 |     |\___ ns.cistron.nl [nl.eu.org] (195.64.65.25) (cached)
 |     |\___ ns.lf.net [nl.eu.org] (194.64.4.1) * * * 
 |     |\___ ns.eu.org [nl.eu.org] (137.194.2.218) Lame server 
 |     |\___ ns2.ispi.net [nl.eu.org] (206.131.193.15) (cached)
 |     |\___ ns.patriots.net [nl.eu.org] (206.131.200.40) (cached)
 |      \___ auth1.dns.elm.net [nl.eu.org] (206.131.200.70) (cached)
[...]
```
The DNS server ns.eu.org is according to RELAY-1.FTEL.CO.UK authoritive for nl.eu.org, but the server doesn't return any answer records. It does however return authority records in which it has itself in it.

The *'s in the output means that there wasn't an answer on the request. By default there is three retries.

####**Multiple additional records, or absence of them**

If there are no additional records for a DNS server, the IP address is being retrieved via a standard gethostbyname().

If there are multiple additional records for a DNS server they are both tested. For example with munnari.OZ.au:

```
[~] edwin@k7>dnstracer www.telstra.com.au
Tracing to www.telstra.com.au via 127.0.0.1, timeout 15 seconds
127.0.0.1 (127.0.0.1) 
 |\___ NS.UU.NET [au] (137.39.1.3) 
 |     |\___ yalumba.connect.com.au [com.au] (203.8.183.1) Got answer
 |     |     |\___ muwaya.ucs.unimelb.EDU.au [telstra.com.au] (128.250.20.2) Got authoritative answer 
 |     |     |\___ munnari.OZ.au [telstra.com.au] (128.250.1.21) Got authoritative answer 
 |     |     |\___ munnari.OZ.au [telstra.com.au] (128.250.22.2) Got authoritative answer 
 |     |     |\___ ns2.telstra.com.au [telstra.com.au] (202.12.144.11) Got authoritative answer 
 |     |      \___ ns.telstra.com.au [telstra.com.au] (202.12.144.10) Got authoritative answer 
[...]
```
####**Authoritative and non-authoritative answers**

Authoritative answers are answers coming from the server which is authoritative for the zone. If the answer is cached by other servers (which is the nature of the DNS system), then the answer is still valid but non-authoritative.

See also that yalumba.connect.com.au doesn't return an authoritative answer, but it knows the answer. The authoritative answer came from one of the servers below it.

```
[~] edwin@k7>dnstracer www.telstra.com.au
Tracing to www.telstra.com.au via 127.0.0.1, timeout 15 seconds
127.0.0.1 (127.0.0.1) 
 |\___ NS.UU.NET [au] (137.39.1.3) 
 |     |\___ yalumba.connect.com.au [com.au] (203.8.183.1) Got answer
 |     |     |\___ muwaya.ucs.unimelb.EDU.au [telstra.com.au] (128.250.20.2) Got authoritative answer 
 |     |     |\___ munnari.OZ.au [telstra.com.au] (128.250.1.21) Got authoritative answer 
[...]
```

Links
-------
