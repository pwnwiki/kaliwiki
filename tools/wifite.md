# wifite

Notes
-------
Automated wireless auditor. Wifite is a python script which automates the WEP and WPA cracking process with aircrack-ng tools.


Help Text
-------
```
  .;'                     `;,    
 .;'  ,;'             `;,  `;,   WiFite v2 (r85)
.;'  ,;'  ,;'     `;,  `;,  `;,  
::   ::   :   ( )   :   ::   ::  automated wireless auditor
':.  ':.  ':. /_\ ,:'  ,:'  ,:'  
 ':.  ':.    /___\    ,:'  ,:'   designed for Linux
  ':.       /_____\      ,:'     
           /       \             

   COMMANDS
	-check <file>	check capfile <file> for handshakes.
	-cracked    	display previously-cracked access points

   GLOBAL
	-all         	attack all targets.              [off]
	-i <iface>  	wireless interface for capturing [auto]
	-mac         	anonymize mac address            [off]
	-c <channel>	channel to scan for targets      [auto]
	-e <essid>  	target a specific access point by ssid (name)  [ask]
	-b <bssid>  	target a specific access point by bssid (mac)  [auto]
	-showb       	display target BSSIDs after scan               [off]
	-pow <db>   	attacks any targets with signal strenghth > db [0]
	-quiet       	do not print list of APs during scan           [off]


   WPA
	-wpa        	only target WPA networks (works with -wps -wep)   [off]
	-wpat <sec>   	time to wait for WPA attack to complete (seconds) [500]
	-wpadt <sec>  	time to wait between sending deauth packets (sec) [10]
	-strip      	strip handshake using tshark or pyrit             [off]
	-crack <dic>	crack WPA handshakes using <dic> wordlist file    [off]
	-dict <file>	specify dictionary to use when cracking WPA [phpbb.txt]
	-aircrack   	verify handshake using aircrack [on]
	-pyrit      	verify handshake using pyrit    [off]
	-tshark     	verify handshake using tshark   [on]
	-cowpatty   	verify handshake using cowpatty [off]

   WEP
	-wep        	only target WEP networks [off]
	-pps <num>  	set the number of packets per second to inject [600]
	-wept <sec> 	sec to wait for each attack, 0 implies endless [600]
	-chopchop   	use chopchop attack      [on]
	-arpreplay  	use arpreplay attack     [on]
	-fragment   	use fragmentation attack [on]
	-caffelatte 	use caffe-latte attack   [on]
	-p0841      	use -p0841 attack        [on]
	-hirte      	use hirte (cfrag) attack [on]
	-nofakeauth 	stop attack if fake authentication fails    [off]
	-wepca <n>  	start cracking when number of ivs surpass n [10000]
	-wepsave    	save a copy of .cap files to this directory [off]

   WPS
	-wps       	only target WPS networks         [off]
	-wpst <sec>  	max wait for new retry before giving up (0: never)  [660]
	-wpsratio <per>	min ratio of successful PIN attempts/total tries    [0]
	-wpsretry <num>	max number of retries for same PIN before giving up [0]

   EXAMPLE
	./wifite.py -wps -wep -c 6 -pps 600

```

Example Usage
-------


```

```

Links
-------
[Wifite Google project](https://code.google.com/p/wifite/)

[Wifite GitHub project](https://github.com/derv82/wifite)
