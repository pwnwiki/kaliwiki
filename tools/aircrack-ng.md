# aircrack-ng  

Notes
-------

 * Version: 1.2-beta2 release  
 * Kali Linux Verison: 1.0.5  
 * Developers: Jaime Penalba & Alvaro


**Purpose**: Aircrack-ng is an 802.11 WEP and WPA-PSK keys cracking program that can recover keys once enough data packets have been captured. It implements the standard FMS attack along with some optimizations like KoreK attacks, as well as the all-new PTW attack, thus making the attack much faster compared to other WEP cracking tools.

# Help Text
-----------

# Suite Tools:<br>
    [- airbase-ng](#airbase-ng)  
    [- aircrack-ng](#aircrack-ng)  
    [- airdecap-ng](#airdecap)  
    [- airdecloak-ng](#airdecloak-ng)  
    [- airdriver-ng](#airdriver-ng)  
    [- airdrop-ng](#airdrop-ng)  
    [- aireplay-ng](#aireplay-ng)  
    [- airgraph-ng](#airgraph-ng)  
    [- airmon-ng](#airmon-ng)  
    [- airodump-ng](#airodump-ng)  
    [- airolib-ng](#airolib-ng)  
    [- airserv-ng](#airsery-ng)  
    [- airtun-ng](#airtun-ng)  
    [- besside-ng](#besside-ng)  
    [- easside-ng](#easside-ng)  
    [- packetforge-ng](#packetforge-ng)  
    [- tkiptun-ng](#tkiptun-ng)  
    [- wesside-ng](#wesside-ng)  
	
Info:

# airbase-ng  
# aircrack-ng  
# airdecap-ng  
# airdecloak-ng  
# airdriver-ng  
# airdrop-ng  
# aireplay-ng  
# airgraph-ng  
# airmon-ng  
Description:

This script can be used to enable monitor mode on wireless interfaces. It may also be used to go back from monitor mode to managed mode. Entering the airmon-ng command without parameters will show the interfaces status.  

	* `airmon-ng <start|stop> <interface> [channel] or airmon-ng <check|check kill>`  
	 
	 Where:  

    * `<start|stop> indicates if you wish to start or stop the interface. (Mandatory)`  
    * `<interface> specifies the interface. (Mandatory)`  
    * `[channel] optionally set the card to a specific channel. (Optional)`  
    * `<check|check kill> “check” will show any processes that might interfere with the aircrack-ng suite. It is strongly recommended that these processes be eliminated prior to using the aircrack-ng suite. “check kill” will check and kill off processes that might interfere with the aircrack-ng suite. For “check kill” see`  

# airodump-ng  
Description  

Airodump-ng is used for packet capturing of raw 802.11 frames and is particularly suitable for collecting WEP IVs (Initialization Vector) for the intent of using them with aircrack-ng. If you have a GPS receiver connected to the computer, airodump-ng is capable of logging the coordinates of the found access points.  
Additionally, airodump-ng writes out several files containing the details of all access points and clients seen.  

usage: airodump-ng <options> <interface>[,<interface>,...]

Options:  
    --ivs               : Save only captured IVs
    --gpsd              : Use GPSd
    --write    <prefix> : Dump file prefix
    -w                  : same as --write
    --beacons           : Record all beacons in dump file
    --update     <secs> : Display update delay in seconds
    --showack           : Prints ack/cts/rts statistics
    -h                  : Hides known stations for --showack
    -f          <msecs> : Time in ms between hopping channels
    --berlin     <secs> : Time before removing the AP/client
                          from the screen when no more packets
                          are received (Default: 120 seconds)
    -r           <file> : Read packets from that file
    -x          <msecs> : Active Scanning Simulation
    --output-format  
              `<formats> : Output format. Possible values:  
                          pcap, ivs, csv, gps, kismet, netxml  
                          Short format "-o"  
                          The option can be specified multiple times.  In this case, each file format  
                          specified will be output.  Only ivs or pcap can be used, not both.  

Filter options:  
    --encrypt   <suite> : Filter APs by cipher suite  
    --netmask <netmask> : Filter APs by mask  
    --bssid     <bssid> : Filter APs by BSSID  
    -a                  : Filter unassociated clients  

By default, airodump-ng hop on 2.4Ghz channels.  
You can make it capture on other/specific channel(s) by using:    
    --channel <channels>: Capture on specific channels  
    --band <abg>        : Band on which airodump-ng should hop  
    -C    <frequencies> : Uses these frequencies in MHz to hop  
    --cswitch  <method> : Set channel switching method`  
                  0     : FIFO (default)  
                  1     : Round Robin  
                  2     : Hop on last  
    -s                  : same as --cswitch  

    --help              : Displays this usage screen  
						  
# airolib-ng  
# airserv-ng  
# airtun-ng  
# besside-ng  
# packetforge-ng  
# tkiptun-ng  
# wesside-ng  

# Example Usage 




Resource Page: http://www.aircrack-ng.org/resources.html

Tutorial Page: http://www.aircrack-ng.org/doku.php?id=tutorial
