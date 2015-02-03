# Tool Name

Notes
-------


Help Text
-------
```
rtl_adsb, a simple ADS-B decoder

Use:	rtl_adsb [-R] [-g gain] [-p ppm] [output file]
	[-d device_index (default: 0)]
	[-V verbove output (default: off)]
	[-S show short frames (default: off)]
	[-Q quality (0: no sanity checks, 0.5: half bit, 1: one bit (default), 2: two bits)]
	[-e allowed_errors (default: 5)]
	[-g tuner_gain (default: automatic)]
	[-p ppm_error (default: 0)]
	filename (a '-' dumps samples to stdout)
	 (omitting the filename also uses stdout)

Streaming with netcat:
	rtl_adsb | netcat -lp 8080
	while true; do rtl_adsb | nc -lp 8080; done
Streaming with socat:
	rtl_adsb | socat -u - TCP4:sdrsharp.com:47806

```

Example Usage
-------


```

```

Links
-------
[Ubuntu Trusty rtl_adsb manpage](http://manpages.ubuntu.com/manpages/trusty/man1/rtl_adsb.1.html)
