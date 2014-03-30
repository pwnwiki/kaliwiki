# p0f

Notes
-------
"P0f is a tool that utilizes an array of sophisticated, purely passive traffic fingerprinting mechanisms to identify the players behind any incidental TCP/IP communications (often as little as a single normal SYN) without interfering in any way. Version 3 is a complete rewrite of the original codebase, incorporating a significant number of improvements to network-level fingerprinting, and introducing the ability to reason about application-level payloads (e.g., HTTP).
Some of p0f's capabilities include:

 * Highly scalable and extremely fast identification of the operating system and software on both endpoints of a vanilla TCP connection - especially in settings where NMap probes are blocked, too slow, unreliable, or would simply set off alarms.
 * Measurement of system uptime and network hookup, distance (including topology behind NAT or packet filters), user language preferences, and so on.
 * Automated detection of connection sharing / NAT, load balancing, and application-level proxying setups.
 * Detection of clients and servers that forge declarative statements such as X-Mailer or User-Agent.

"The tool can be operated in the foreground or as a daemon, and offers a simple real-time API for third-party components that wish to obtain additional information about the actors they are talking to.
Common uses for p0f include reconnaissance during penetration tests; routine network monitoring; detection of unauthorized network interconnects in corporate environments; providing signals for abuse-prevention tools; and miscellanous forensics."

From: http://lcamtuf.coredump.cx/p0f3/


Help Text
-------
```
p0f: invalid option -- 'h'

Usage: p0f [ -f file ] [ -i device ] [ -s file ] [ -o file ]
       [ -w file ] [ -Q sock [ -0 ] ] [ -u user ] [ -FXVNDUKASCMROqtpvdlrx ]
       [ -c size ] [ -T nn ] [ -e nn ] [ 'filter rule' ]
  -f file   - read fingerprints from file
  -i device - listen on this device
  -s file   - read packets from tcpdump snapshot
  -o file   - write to this logfile (implies -t)
  -w file   - save packets to tcpdump snapshot
  -u user   - chroot and setuid to this user
  -Q sock   - listen on local socket for queries
  -0        - make src port 0 a wildcard (in query mode)
  -e ms     - pcap capture timeout in milliseconds (default: 1)
  -c size   - cache size for -Q and -M options
  -M        - run masquerade detection
  -T nn     - set masquerade detection threshold (1-200)
  -V        - verbose masquerade flags reporting
  -F        - use fuzzy matching (do not combine with -R)
  -N        - do not report distances and link media
  -D        - do not report OS details (just genre)
  -U        - do not display unknown signatures
  -K        - do not display known signatures (for tests)
  -S        - report signatures even for known systems
  -A        - go into SYN+ACK mode (semi-supported)
  -R        - go into RST/RST+ACK mode (semi-supported)
  -O        - go into stray ACK mode (barely supported)
  -r        - resolve host names (not recommended)
  -q        - be quiet - no banner
  -v        - enable support for 802.1Q VLAN frames
  -p        - switch card to promiscuous mode
  -d        - daemon mode (fork into background)
  -l        - use single-line output (easier to grep)
  -x        - include full packet dump (for debugging)
  -X        - display payload string (useful in RST mode)
  -C        - run signature collision check
  -t        - add timestamps to every entry

  'Filter rule' is an optional pcap-style BPF expression (man tcpdump).


```

Example Usage
-------

Links
-------

