# sqlninja

Notes
-------

Help Text
-------
```
Sqlninja rel. 0.2.6-r1
Copyright (C) 2006-2011 icesurfer <r00t@northernfortress.net>
Usage: /usr/bin/sqlninja
	-m <mode> : Required. Available modes are:
	    t/test - test whether the injection is working
	    f/fingerprint - fingerprint user, xp_cmdshell and more
	    b/bruteforce - bruteforce sa account
	    e/escalation - add user to sysadmin server role
	    x/resurrectxp - try to recreate xp_cmdshell
	    u/upload - upload a .scr file
	    s/dirshell - start a direct shell
	    k/backscan - look for an open outbound port
	    r/revshell - start a reverse shell
	    d/dnstunnel - attempt a dns tunneled shell
	    i/icmpshell - start a reverse ICMP shell
	    c/sqlcmd - issue a 'blind' OS command
	    m/metasploit - wrapper to Metasploit stagers
	-f <file> : configuration file (default: sqlninja.conf)
	-p <password> : sa password
	-w <wordlist> : wordlist to use in bruteforce mode (dictionary method
	                only)
	-g : generate debug script and exit (only valid in upload mode)
	-v : verbose output
	-d <mode> : activate debug
	    1 - print each injected command
	    2 - print each raw HTTP request
	    3 - print each raw HTTP response
	    all - all of the above
	...see sqlninja-howto.html for details

```

Example Usage
-------

Links
-------
[SQLninja](http://sqlninja.sourceforge.net/index.html)

