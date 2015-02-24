# aircrack-ng

Notes
-------
Aircrack-ng is an 802.11 WEP and WPA-PSK keys cracking program that can recover keys once enough data packets have been captured. It implements the standard FMS attack along with some optimizations like KoreK attacks, as well as the PTW attack, thus making the attack much faster compared to other WEP cracking tools.


Help Text
-------
```
Aircrack-ng 1.2 beta3 - (C) 2006-2013 Thomas d'Otreppe
  http://www.aircrack-ng.org

  usage: aircrack-ng [options] <.cap / .ivs file(s)>

  Common options:

      -a <amode> : force attack mode (1/WEP, 2/WPA-PSK)
      -e <essid> : target selection: network identifier
      -b <bssid> : target selection: access point's MAC
      -p <nbcpu> : # of CPU to use  (default: all CPUs)
      -q         : enable quiet mode (no status output)
      -C <macs>  : merge the given APs to a virtual one
      -l <file>  : write key to file

  Static WEP cracking options:

      -c         : search alpha-numeric characters only
      -t         : search binary coded decimal chr only
      -h         : search the numeric key for Fritz!BOX
      -d <mask>  : use masking of the key (A1:XX:CF:YY)
      -m <maddr> : MAC address to filter usable packets
      -n <nbits> : WEP key length :  64/128/152/256/512
      -i <index> : WEP key index (1 to 4), default: any
      -f <fudge> : bruteforce fudge factor,  default: 2
      -k <korek> : disable one attack method  (1 to 17)
      -x or -x0  : disable bruteforce for last keybytes
      -x1        : last keybyte bruteforcing  (default)
      -x2        : enable last  2 keybytes bruteforcing
      -X         : disable  bruteforce   multithreading
      -y         : experimental  single bruteforce mode
      -K         : use only old KoreK attacks (pre-PTW)
      -s         : show the key in ASCII while cracking
      -M <num>   : specify maximum number of IVs to use
      -D         : WEP decloak, skips broken keystreams
      -P <num>   : PTW debug:  1: disable Klein, 2: PTW
      -1         : run only 1 try to crack key with PTW

  WEP and WPA-PSK cracking options:

      -w <words> : path to wordlist(s) filename(s)

  WPA-PSK options:

      -E <file>  : create EWSA Project file v3
      -J <file>  : create Hashcat Capture file
      -S         : WPA cracking speed test

  Other options:

      -u         : Displays # of CPUs & MMX/SSE support
      --help     : Displays this usage screen

```

Example Usage
-------

```

```

Links
-------
[Official site](http://aircrack-ng.org/)

[Aircrack Documentation](http://aircrack-ng.org/documentation.html)

[Aircrack Getting started Tutorial](http://aircrack-ng.org/doku.php?id=getting_started)

[Aircrack Ubuntu Trusty manpage](http://manpages.ubuntu.com/manpages/trusty/en/man1/aircrack-ng.1.html)
