# ace Automated Corporate (Data) Enumerator

Notes
-------

Help Text
-------
```
ACE v1.10: Automated Corporate (Data) Enumerator
Usage: ace [-i interface] [ -m mac address ] [ -t tftp server ip address | -c cdp mode | -v voice vlan id | -r vlan interface | -d verbose mode ]

-i <interface> (Mandatory) Interface for sniffing/sending packets
-m <mac address> (Mandatory) MAC address of the victim IP phone 
-t <tftp server ip> (Optional) tftp server ip address 
-c <cdp mode 0|1 > (Optional) 0 CDP sniff mode, 1 CDP spoof mode 
-v <voice vlan id> (Optional) Enter the voice vlan ID 
-r <vlan interface> (Optional) Removes the VLAN interface 
-d 		    (Optional) Verbose | debug mode 

Example Usages: 
Usage requires MAC Address of IP Phone supplied with -m option
Usage:  ace -t <TFTP-Server-IP> -m <MAC-Address>

Mode to automatically discover TFTP Server IP via DHCP Option 150 (-m)
Example:  ace -i eth0 -m 00:1E:F7:28:9C:8e

Mode to specify IP Address of TFTP Server
Example:  ace -i eth0 -t 192.168.10.150 -m 00:1E:F7:28:9C:8e

Mode to specify the Voice VLAN ID
Example: ace -i eth0 -v 96 -m 00:1E:F7:28:9C:8E

Verbose mode 
Example: ace -i eth0 -v 96 -m 00:1E:F7:28:9C:8E -d

Mode to remove vlan interface
Example: ace -r eth0.96 

Mode to auto-discover voice vlan ID in the listening mode for CDP
Example: ace -i eth0 -c 0 -m 00:1E:F7:28:9C:8E

Mode to auto-discover voice vlan ID in the spoofing mode for CDP
Example: ace -i eth0 -c 1 -m 00:1E:F7:28:9C:8E

```

Example Usage
-------

Links
-------

