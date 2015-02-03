# netdiscover  

Notes
-------

 * Version: 0.3-beta7 [Active/passive arp reconnaissance tool]  
 * Kali Linux Verison: 1.0.5  
 * Developers: Jaime Penalba & Alvaro

**Dependency**: libnet 1.1.x & libpcap

**Purpose**: Netdiscover is an active/passive address reconnaissance tool, mainly developed for those wireless network without dhcp server, when you are wardriving. It can be also used on hub/switched networks.  It can passively detect online hosts, or search for them, by actively sending arp requests, it can also be used to inspect your network arp traffic, or find network addresses using auto scan mode, which will scan for common local networks. 

Help Text
----------
```
Usage: netdiscover [-i device] [-r range | -l file | -p] [-s time] [-n node] [-c count] [-f] [-d] [-S] [-P] [-C]  
  -i device:  
	The network interface to sniff and inject packets. If no  interface is specified, first available will be used.
  -r range:  
	Scan a given range instead of auto scan. 192.168.6.0/24,/16,/8.  
  -l file:  
	Scan the list of ranges contained into the given file, it must contain one range per line.  
  -p passive mode:  
	Enable  passive mode. In passive mode, netdiscover does not send anything, but does only sniff.
  -F filter:  
	Customize pcap filter expression (default: "arp")  
  -s time: 
	Sleep given time in milliseconds between each arp request injection. (default 1) 
  -n node: 
	Last ip octet of the source ip used for scanning. You can change it  if  the  default  host is already used. (allowed range: 2 to 253, default 66)  
  -c count: 
	Number of times to send each arp request. Useful for networks with packet loss, so it will scan given times for each host.  
  -f 
	Enable fast mode scan. This will only scan for .1, .100 and .254 on each network. This mode is usefull while searching for ranges being  used.  After you found such range you can make a specific range scan to find online boxes.  
  -d 
	Ignore configuration files at home dir, this will  use  defaults ranges  and ips for autoscan and fast mode. See below for information about configuration files.    
  -S 
	Enable sleep time suppression between each request. If set, netdiscover  will  sleep  after having scanned 255 hosts instead of
sleeping after each one.  This mode was used in netdiscover  0.3 beta4  and  before.  Avoid  this  option in networks with packet loss, or in wireless  networks  with  low  signal  level.  (also called hardcore mode)  
  -P 
	Produces output suitable to be redirected  into  a  file  or  be parsed  by  another  program, instead of using interactive mode. Enabling this option, netdiscover will stop after scanning given ranges.   
  -L 
	When  using -P, continue program execution after the active scan phase to capture ARP packets passively.    

If -r, -l or -p are not enabled, netdiscover will scan for common lan addresses.  

On screen usage keys:  

  h      Show help screen  
  j      Scroll down (or down arrow)  
  k      Scroll up (or up arrow)  
  a      Show arp replys list  
  r      Show arp requests list  
  q      Close help screen or end application  

```

Configuration Files
--------------------

There  are  2  configuration files that netdiscover will look for, each time it is executed, if file doesn't exist it will use  default  values.

You  can use the -d switch to disable reading and loading configuration files.

 * **~/.netdiscover/ranges** - This file contains a list of ranges (one per line) used for auto scan mode instead of default ranges. By default netdiscover will use a list of common ranges used on local networks.
  * Example:
```
192.168.21.0/24
172.26.0.0/16
10.0.0.0/8
```

 * **~/.netdiscover/fastips** - List containing the last octet of the ips to be scanned on each subnet, when using fast mode, by default (1,100,154).

  * Example:
```
1
10
25
254
```

Example Usage
---------------

Scan a class C network, to see wich hosts are up:

 * `netdiscover -i etho -r 192.168.1.0/24`
 * `netdiscover i wlan0 -r 10.0.0.1/16`

Auto scan common networks:

 * `netdiscover -i eth1`

Don't send ARP requests, listen only:

 * `netdiscover -i wlan0 -p`

Auto scan in fast mode:

 * `netdiscover -i eth0 -f`

Scan with sleep in-between:

 * `netdiscover -i eth1 -s 30`  

Scan range with count:

 * `netdiscover -r 192.168.1.0/24 -c 50`  

Send output to a file:

Note: netdiscover will stop after scanning given ranges

 * `netdiscover -r 192.168.1.0/24 -P`

Send output to a file and continue scanning:

 * `netdiscover -i eth0 -r 192.168.1.0/24 -L -P`

Scan list of range from a file:

 * `netdiscover -i eth1 -l iprange.txt`  

Filter pcap expression:

Note: looking for system only using telnet

 * `netdiscover -i eth0 -r 10.0.0.1/16 -s 20 -F telnet`  


Links
----------  

* Source: http://sourceforge.net/projects/netdiscover/  
* Source: http://nixgeneration.com/~jaime/netdiscover/  
* Video: https://www.youtube.com/watch?v=35BvdXSrfZk  
* Video: https://www.youtube.com/watch?v=4Ahoj3YafMU
