Tool: Netdiscover
Version: 0.3-beta6
Kali Linux Verison: 1.0.5
Developers: Jaime Penalba & Alvaro

Purpose: Netdiscover is an active/passive address reconnaissance tool, mainly developed for those wireless network without dhcp server, when you are wardriving. It can be also used on hub/switched networks.  It can passively detect online hosts, or search for them, by actively sending arp requests, it can also be used to inspect your network arp traffic, or find network addresses using auto scan mode, which will scan for common local networks. 

Command line usage & parameters:

Usage: netdiscover [-i device] [-r range | -p] [-s time] [-n node] [-c count] [-f] [-S]
  -i device: your network device
  -r range: scan a given range instead of auto scan. 192.168.6.0/24,/16,/8
  -p passive mode do not send anything, only sniff
  -s time: time to sleep between each arp request (miliseconds)
  -c count: number of times to send each arp reques (for nets with packet loss)
  -n node: last ip octet used for scanning (from 2 to 253)
  -S enable sleep time supression betwen each request (hardcore mode)
  -f enable fastmode scan, saves a lot of time, recommended for auto

If -p or -r arent enabled, netdiscover will scan for common lan addresses

On screen usage keys:

  h      Show help screen
  j      Scroll down (or down arrow)
  k      Scroll up (or up arrow)
  a      Show arp replys list
  r      Show arp requests list
  q      Close help screen or end application

Some examples of usage:

    Scan a class C network, to see wich hosts are up
    # netdiscover -i etho -r 192.168.1.0/24
    # netdiscover i wlan0 -r 10.0.0.1/16

    Auto scan common networks
    # netdiscover -i eth1

    Dont send arp requests, listen only
    # netdiscover -i wlan0 -p

    Auto scan in fast mode
    # netdiscover -i eth0 -f

    Scan with sleep inbetween
    # netdiscover -i eth1 -s 30

    Scan range with count 
    # netdiscover -r 192.168.1.0/24 -c 50



Dependency: libnet 1.1.x & libpcap

Audience: Penetration testing, Wireless Testing, System Administrator

website: http://sourceforge.net/projects/netdiscover/
webiste: http://nixgeneration.com/~jaime/netdiscover/
youtube: https://www.youtube.com/watch?v=35BvdXSrfZk/

test
youtube: https://www.youtube.com/watch?v=4Ahoj3YafMU&feature=player_embedded
