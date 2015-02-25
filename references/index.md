## Kali basic

#### Change region to increase Tx power:
- check region: `iw reg get`
- set region `iw reg set BO`

### Init

- enable monitor mode: `airmon-ng start wlan0`

#### Up interface and connect to Network:

- Show devices:  `iw dev`
- Check device status: `ip link show wlan0`
- Enable a network interface:  `ifconfig wlan0 up` or `ip link set wlan0 up`
- Check the connection status – WiFi network from command line `iw wlan0 link`


>Based on [http://www.blackmoreops.com/2014/09/18/connect-to-wifi-network-from-command-line-in-linux/](http://www.blackmoreops.com/2014/09/18/connect-to-wifi-network-from-command-line-in-linux/)

- Set IP address: `ifconfig wlan0 192.168.0.77` or `ip address add 192.168.0.77 dev wlan0`


### Scan:

- Show all networks around `iw waln0 scan` or `iwlist wlan0 scan`
    - grep most useful info from there: `iw wlan0 scan | grep -E '(SSID|^BSS|WPS|WEP|WPA|RSN)|signal'`
- Show networks with open WPS: `wash -i mon0`

- Show hidden ESSID:
    1. Scan channel n: `airodump-ng -c n  mon0`
    2. Make a deauth attack: `aireplay-ng -0 2 -a $SSID mon0`


### WPS attack:
- Reaver attack: `reaver -i mon0 -b $SSID -vv -d 5 -N -S -E`

- Sniff-detecting: `nmap --script=sniffer-detect 192.168.x.0/24`

### Resolve errors: 

- Durring `ifconfig wlan0 up` appears error 'RTNETLINK answers: Operation not possible due to RF-kill'
    >http://www.geekmind.net/2011/01/linux-wifi-operation-not-possible-due.html

        rfkill list all 
      
> if "Soft blocked: yes" -> then

```
      rfkill unblock wifi
      rfkill list all
```
