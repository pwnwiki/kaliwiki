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
-------------
Search for the A record of www.mavetju.org on your local nameserver:

dnstracer www.mavetju.org

Search for the MX record of mavetju.org on the root-nameservers:

dnstracer "-s" . "-q" mx mavetju.org

Search for the PTR record (hostname) of 212.204.230.141:

dnstracer "-q" ptr 141.230.204.212.in-addr.arpa

And for IPv6 addresses:

dnstracer "-q" ptr "-s" . "-o"
2.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.6.4.0.2.0.0.0.0.8.b.0.e.f.f.3.ip6.int

Links
-----
