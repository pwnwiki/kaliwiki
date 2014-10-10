# kismet

Notes
-------
Kismet is an 802.11 layer2 wireless network detector, sniffer, and intrusion detection system. Kismet will work with any wireless card which supports raw monitoring (rfmon) mode, and (with appropriate hardware) can sniff 802.11b, 802.11a, 802.11g, and 802.11n traffic.
Kismet also supports plugins which allow sniffing other media such as DECT.


Help Text
-------
```
Usage: /usr/bin/kismet_server [OPTION]
Nearly all of these options are run-time overrides for values in the
kismet.conf configuration file.  Permanent changes should be made to
the configuration file.
 *** Generic Options ***
 -v, --version                Show version
 -f, --config-file <file>     Use alternate configuration file
     --no-line-wrap           Turn of linewrapping of output
                              (for grep, speed, etc)
 -s, --silent                 Turn off stdout output after setup phase
     --daemonize              Spawn detatched in the background
     --no-plugins             Do not load plugins
     --no-root				  Do not start the kismet_capture binary 
                               when not running as root.  For no-priv 
                               remote capture ONLY.

 *** Kismet Client/Server Options ***
 -l, --server-listen          Override Kismet server listen options

 *** Kismet Remote Drone Options ***
     --drone-listen           Override Kismet drone listen options

 *** Dump/Logging Options ***
 -T, --log-types <types>      Override activated log types
 -t, --log-title <title>      Override default log title
 -p, --log-prefix <prefix>    Directory to store log files
 -n, --no-logging             Disable logging entirely

 *** Packet Capture Source Options ***
 -c, --capture-source         Specify a new packet capture source
                              (Identical syntax to the config file)
 -C, --enable-capture-sources Enable capture sources (comma-separated
                              list of names or interfaces)

 *** Kismet Net Tracking Options ***
     --filter-tracker         Tracker filtering

 *** Kismet GPS Options ***
     --use-gpsd-gps (h:p)     Use GPSD-controlled GPS at host:port
                              (default: localhost:2947)
     --use-nmea-gps (dev)     Use local NMEA serial GPS on device
                              (default: /dev/ttyUSB0)
     --use-virtual-gps
                (lat,lon,alt) Use a virtual fixed-position gps record
     --gps-modelock <t:f>     Force broken GPS units to act as if they
                              have a valid signal (true/false)
     --gps-reconnect <t:f>    Reconnect if a GPS device fails
                              (true/false)
```

Example Usage
-------


```

```

Links
-------
[Official site](https://www.kismetwireless.net/)

[Kismet Wikipedia article](http://en.wikipedia.org/wiki/Kismet_(software))
