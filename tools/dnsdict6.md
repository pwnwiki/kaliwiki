# dnsdict6

Notes
-------

Has a pretty good built in list. But the SRV service enumeration doesn't seem to do anything. Ran it against att.com and all I got was:
```
dnsdict6 -t 32 -S att.com
Starting DNS enumeration work on att.com. ...
Starting SRV service enumeration
Estimated time to completion: 1 to 4 minutes
Found 582 services with 1164 entries altogether
```
Then it started brute forcing as it normally would

Help Text
-------
```
dnsdict6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

Syntax: dnsdict6 [-d46] [-s|-m|-l|-x] [-t THREADS] [-D] domain [dictionary-file]

Enumerates a domain for DNS entries, it uses a dictionary file if supplied or a built-in list otherwise. This tool is based on dnsmap by gnucitizen.org.

Options:
 -4      also dump IPv4 addresses
 -t NO   specify the number of threads to use (default: 8, max: 32).
 -D      dump the selected built-in wordlist, no scanning.
 -d      display IPv6 information on NS and MX DNS domain information.
 -S      perform SRV service name guessing
 -[smlx] choose the dictionary size by -s(mall=50), -m(edium=796) (DEFAULT)
 -l(arge=1416), or -x(treme=3211)
```

Example Usage
-------
```
root@kali:~# dnsdict6 google.com
Starting DNS enumeration work on google.com. ...
Starting enumerating google.com. - creating 8 threads for 798 words...
Estimated time to completion: 1 to 2 minutes
www.google.com. => 2607:f8b0:4004:804::1011
ipv6.google.com. => 2607:f8b0:4004:803::1012
mail.google.com. => 2607:f8b0:4004:803::1015
news.google.com. => 2607:f8b0:4004:803::1002
dns.google.com. => 2607:f8b0:4004:803::1002
blog.google.com. => 2607:f8b0:400d:c04::bf

```

Links
-------
* Source: https://www.thc.org/thc-ipv6/
* How-To: http://ultimatepeter.com/how-to-hack-using-dnsdict6-to-enumerate-dns-records-ip-ns-mx-subdomains-etc/
* Video: http://www.youtube.com/watch?v=czJuAshZWho