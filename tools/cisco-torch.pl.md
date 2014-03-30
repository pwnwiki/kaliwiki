# cisco-torch.pl

Notes
-------

Help Text
-------
```
Using config file torch.conf...
Loading include and plugin ...
 version 
usage: ./cisco-torch.pl <options> <IP,hostname,network>

or: ./cisco-torch.pl <options> -F <hostlist>

Available options:
-O <output file>
-A		All fingerprint scan types combined
-t		Cisco Telnetd scan
-s		Cisco SSHd scan
-u		Cisco SNMP scan
-g		Cisco config or tftp file download
-n		NTP fingerprinting scan
-j		TFTP fingerprinting scan
-l <type>	loglevel
		c  critical (default)
		v  verbose
		d  debug
-w		Cisco Webserver scan
-z		Cisco IOS HTTP Authorization Vulnerability Scan
-c		Cisco Webserver with SSL support scan
-b		Password dictionary attack (use with -s, -u, -c, -w , -j or -t only)
-V		Print tool version and exit
examples:	./cisco-torch.pl -A 10.10.0.0/16
		./cisco-torch.pl -s -b -F sshtocheck.txt
		./cisco-torch.pl -w -z 10.10.0.0/16
		./cisco-torch.pl -j -b -g -F tftptocheck.txt
```

Example Usage
-------

Links
-------

