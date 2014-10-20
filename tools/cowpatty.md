# coWPAtty

Notes
-------
Implementation of an offline dictionary attack against WPA/WPA2 networks using PSK-based authentication (e.g. WPA-Personal). 
Many enterprise networks deploy PSK-based authentication mechanisms for WPA/WPA2 since it is much easier than establishing the necessary RADIUS, supplicant and certificate authority architecture needed for WPA-Enterprise authentication. Cowpatty can implement an accelerated attack if a precomputed PMK file is available for the SSID that is being assessed.


Help Text
-------
```
cowpatty 4.6 - WPA-PSK dictionary attack. <jwright@hasborg.com>
cowpatty: Must supply a pcap file with -r

Usage: cowpatty [options]

	-f 	Dictionary file
	-d 	Hash file (genpmk)
	-r 	Packet capture file
	-s 	Network SSID (enclose in quotes if SSID includes spaces)
	-c 	Check for valid 4-way frames, does not crack
	-h 	Print this help information and exit
	-v 	Print verbose information (more -v for more verbosity)
	-V 	Print program version and exit


```

Example Usage
-------


```

```

Links
-------
[Official site](http://www.willhackforsushi.com/?page_id=50)
