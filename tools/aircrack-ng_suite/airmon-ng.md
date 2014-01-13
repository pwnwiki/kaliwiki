AIRMON-NG

Notes
-------

 * Version: 1.2-beta2 release  
 * Kali Linux Verison: 1.0.6  
 * Developers: Thomas d'Otreppe

***Purpose***  -  bash  script designed to turn wireless cards into monitor
       mode.

**SYNOPSIS**
```
       airmon-ng <start|stop> <interface> [channel] airmon-ng <check> [kill]
```
**DESCRIPTION**
```    airmon-ng is script can be used to  enable  monitor  mode  on  wireless
       interfaces. It may also be used to go back from monitor mode to managed
       mode. Entering the airmon-ng command without parameters will  show  the
       interfaces  status.   It can list/kill programs that can interfere with
       the wireless card and set the right sources in  /etc/kismet/kismet.conf
       too.
```
**OPTIONAL PARAMETERS**
```    start <interface> [channel]
              Enable  monitor  mode  on  an interface (and specify a channel).
              Note: Madwifi-ng is a special case, 'start' has to  be  used  on
              wifi  interfaces and 'stop' on ath interfaces.  stop <interface>
              Disable monitor mode and go back to  managed  mode  (except  for
              madwifi-ng where it kills the ath VAP).

       check [kill]
              List  all  possible programs that could interfere with the wire
              less card. If 'kill' is specified, it will try to  kill  all  of
              them.
```

Example Usage
---------------

Display all process that will interfere with wireless card
	* `airmon-ng check`
	
Kill any process that will interfere with wireless card
	* `airmon-ng check kill`
	
Start monitor mode
	* `airmon-ng start wlan0`
	
Start monitor mode on a specific channel
	* `airmon-ng start wlan0 11`
	
Stop monitor mode
	* `airmon-ng stop mon0`