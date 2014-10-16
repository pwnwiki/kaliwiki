# eapmd5pass

Notes
-------
An implementation of an offline dictionary attack against the EAP-MD5 protocol. 
This utility can be used to audit passwords used for EAP-MD5 networks from wireless packet captures, or by manually specifying the challenge, response and associated authentication information.



Help Text
-------
```
eapmd5pass - Dictionary attack against EAP-MD5

Usage: eapmd5pass [ -i <int> | -r <pcapfile> ] [ -w wordfile ] [options]

  -i <iface>	interface name
  -r <pcapfile>	read from a named libpcap file
  -w <wordfile>	use wordfile for possible passwords.
  -b <bssid>	BSSID of target network (default: all)
  -U <username>	Username of EAP-MD5 user.
  -C <chal>	EAP-MD5 challenge value.
  -R <response>	EAP-MD5 response value.
  -E <eapid>	EAP-MD5 response EAP ID value.
  -v		increase verbosity level (max 3)
  -V		version information
  -h		usage information

The "-r" and "[-U|-C|-R|-E]" options are not meant to be used together.  Use -r
when a packet capture is available.  Specify the username, challenge and
response when available through other means.


```

Example Usage
-------


```

```

Links
-------
[Ofiicial site](http://www.willhackforsushi.com/?page_id=67) 

[CRACKING EAP-MD5 WITH EAPMD5PASS AND EAPMD5CRACK Video](http://www.securitytube.net/video/2008)
