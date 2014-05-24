# xprobe2

Notes
-------
xprobe2 is an active operating system fingerprinting tool with a different approach to operating system fingerprinting. xprobe2 relies on fuzzy signature matching, probabilistic guesses, multiple matches simultaneously, and a signature database.

Help Text
-------
```
Xprobe2 v.0.3 Copyright (c) 2002-2005 fyodor@o0o.nu, ofir@sys-security.com, meder@o0o.nu

usage: xprobe2 [options] target
Options:
          -v                       Be verbose
          -r                       Show route to target(traceroute)
          -p <proto:portnum:state> Specify portnumber, protocol and state.
                                   Example: tcp:23:open, UDP:53:CLOSED
          -c <configfile>          Specify config file to use.
          -h                       Print this help.
          -o <fname>               Use logfile to log everything.
          -t <time_sec>            Set initial receive timeout or roundtrip time.
          -s <send_delay>          Set packsending delay (milseconds).
          -d <debuglv>             Specify debugging level.
          -D <modnum>              Disable module number <modnum>.
          -M <modnum>              Enable module number <modnum>.
          -L                       Display modules.
          -m <numofmatches>        Specify number of matches to print.
          -T <portspec>            Enable TCP portscan for specified port(s).
                                   Example: -T21-23,53,110
          -U <portspec>            Enable UDP portscan for specified port(s).
          -f                       force fixed round-trip time (-t opt).
          -F                       Generate signature (use -o to save to a file).
          -X                       Generate XML output and save it to logfile specified with -o.
          -B                       Options forces TCP handshake module to try to guess open TCP port
          -A                       Perform analysis of sample packets gathered during portscan in
                                   order to detect suspicious traffic (i.e. transparent proxies,
                                   firewalls/NIDSs resetting connections). Use with -T.
```

Example Usage
-------
```
$ sudo xprobe2 -v 10.1.1.2
sudo: cannot get working directory

Xprobe2 v.0.3 Copyright (c) 2002-2005 fyodor@o0o.nu, ofir@sys-security.com, meder@o0o.nu

[+] Target is 10.1.1.2
[+] Loading modules.
[+] Following modules are loaded:
[x] [1] ping:icmp_ping  -  ICMP echo discovery module
[x] [2] ping:tcp_ping  -  TCP-based ping discovery module
[x] [3] ping:udp_ping  -  UDP-based ping discovery module
[x] [4] infogather:ttl_calc  -  TCP and UDP based TTL distance calculation
[x] [5] infogather:portscan  -  TCP and UDP PortScanner
[x] [6] fingerprint:icmp_echo  -  ICMP Echo request fingerprinting module
[x] [7] fingerprint:icmp_tstamp  -  ICMP Timestamp request fingerprinting module
[x] [8] fingerprint:icmp_amask  -  ICMP Address mask request fingerprinting module
[x] [9] fingerprint:icmp_port_unreach  -  ICMP port unreachable fingerprinting module
[x] [10] fingerprint:tcp_hshake  -  TCP Handshake fingerprinting module
[x] [11] fingerprint:tcp_rst  -  TCP RST fingerprinting module
[x] [12] fingerprint:smb  -  SMB fingerprinting module
[x] [13] fingerprint:snmp  -  SNMPv2c fingerprinting module
[+] 13 modules registered
[+] Initializing scan engine
[+] Running scan engine
[-] ping:tcp_ping module: no closed/open TCP ports known on 10.1.1.2. Module test failed
[-] ping:udp_ping module: no closed/open UDP ports known on 10.1.1.2. Module test failed
[-] No distance calculation. 10.1.1.2 appears to be dead or no ports known
[+] Host: 10.1.1.2 is up (Guess probability: 50%)
[+] Target: 10.1.1.2 is alive. Round-Trip Time: 0.00039 sec
[+] Selected safe Round-Trip Time value is: 0.00079 sec
[-] fingerprint:tcp_hshake Module execution aborted (no open TCP ports known)
[-] fingerprint:smb need either TCP port 139 or 445 to run
[-] fingerprint:snmp: need UDP port 161 open
[+] Primary guess:
[+] Host 10.1.1.2 Running OS: "Microsoft Windows 2003 Server Standard Edition" (Guess probability: 100%)
[+] Other guesses:
[+] Host 10.1.1.2 Running OS: "Microsoft Windows 2003 Server Enterprise Edition" (Guess probability: 100%)
[+] Host 10.1.1.2 Running OS: "Microsoft Windows XP SP2" (Guess probability: 100%)
[+] Host 10.1.1.2 Running OS: "Microsoft Windows 2000 Workstation" (Guess probability: 100%)
[+] Host 10.1.1.2 Running OS: "Microsoft Windows 2000 Workstation SP1" (Guess probability: 100%)
[+] Host 10.1.1.2 Running OS: "Microsoft Windows 2000 Workstation SP2" (Guess probability: 100%)
[+] Host 10.1.1.2 Running OS: "Microsoft Windows 2000 Workstation SP3" (Guess probability: 100%)
[+] Host 10.1.1.2 Running OS: "Microsoft Windows 2000 Workstation SP4" (Guess probability: 100%)
[+] Host 10.1.1.2 Running OS: "Microsoft Windows 2000 Server" (Guess probability: 100%)
[+] Host 10.1.1.2 Running OS: "Microsoft Windows 2000 Server Service Pack 1" (Guess probability: 100%)
[+] Cleaning up scan engine
[+] Modules deinitialized
[+] Execution completed.
```
* taken from aldeid[5]


Links
-------
1. [sourceforge](http://sourceforge.net/projects/xprobe/files/xprobe2/)
1. [darknet](http://www.darknet.org.uk/2008/05/xprobe2-active-os-fingerprinting-tool/)
1. [SANS](http://www.sans.org/security-resources/idfaq/xprobe.php)
1. [Blackhat Paper](http://www.blackhat.com/presentations/bh-federal-03/bh-fed-03-arkin.pdf)
1. [aldeid](http://www.aldeid.com/wiki/Xprobe2)