AIRCRACK-NG

NAME
       aircrack-ng - a 802.11 WEP / WPA-PSK key cracker

SYNOPSIS
       aircrack-ng [options] <.cap / .ivs file(s)>

DESCRIPTION
       aircrack-ng is an 802.11 WEP and WPA/WPA2-PSK key cracking program.
       It can recover the WEP key once enough encrypted packets have been capâ€
       tured with airodump-ng. This part of the aircrack-ng  suite  determines
       the  WEP key using two fundamental methods. The first method is via the
       PTW approach (Pyshkin, Tews, Weinmann). The main advantage of  the  PTW
       approach  is  that  very few data packets are required to crack the WEP
       key. The second method is the FMS/KoreK method.  The  FMS/KoreK  method
       incorporates  various  statistical  attacks to discover the WEP key and
       uses these in combination with brute forcing.
       Additionally, the program offers a dictionary  method  for  determining
       the WEP key. For cracking WPA/WPA2 pre-shared keys, a wordlist (file or
       stdin) or an airolib-ng has to be used.

OPTIONS
       Common options:

       -a <amode>
              Force the attack mode, 1 or wep for WEP and 2 or  wpa  for  WPA-
              PSK.

       -e <essid>
              Select  the  target  network  based on the ESSID. This option is
              also required for WPA cracking if the SSID is cloacked. For SSID
              containing    special   characters,   see   http://www.aircrack-
              ng.org/doku.php?id=faq#how_to_use_spaces_double_quote_and_sinâ€
              gle_quote_etc._in_ap_names

       -b <bssid> or --bssid <bssid>
              Select the target network based on the access point MAC address.

       -p <nbcpu>
              Set  this option to the number of CPUs to use (only available on
              SMP systems). By default, it uses all available CPUs

       -q     If set, no status information is displayed.

       -C <macs> or --combine <macs>
              Merges all those APs MAC (separated by a comma) into  a  virtual
              one.

       -l <file>
              Write the key into a file.

       -E <file>
              Create  Elcomsoft  Wireless Security Auditor (EWSA) Project file
              v3.02.

       Static WEP cracking options:

       -c     Search alpha-numeric characters only.

       -t     Search binary coded decimal characters only.

       -h     Search the numeric key for Fritz!BOX

       -d <mask> or --debug <mask>
              Specify mask of the key. For example: A1:XX:CF

       -m <maddr>
              Only keep the IVs  coming  from  packets  that  match  this  MAC
              address.  Alternatively, use -m ff:ff:ff:ff:ff:ff to use all and
              every IVs, regardless of the network (this  disables  ESSID  and
              BSSID filtering).

       -n <nbits>
              Specify  the  length  of  the  key:  64  for 40-bit WEP, 128 for
              104-bit WEP, etc., until 512 bits of length. The  default  value
              is 128.

       -i <index>
              Only keep the IVs that have this key index (1 to 4). The default
              behaviour is to ignore the key index in the packet, and use  the
              IV regardless.

       -f <fudge>
              By  default,  this  parameter is set to 2. Use a higher value to
              increase the bruteforce level: cracking will take more time, but
              with a higher likelihood of success.

       -k <korek>
              There  are 17 KoreK attacks. Sometimes one attack creates a huge
              false positive that prevents the key from being found, even with
              lots  of  IVs.  Try -k 1, -k 2, ... -k 17 to disable each attack
              selectively.

       -x or -x0
              Disable last keybytes bruteforce (not advised).

       -x1    Enable last keybyte bruteforcing (default)

       -x2    Enable last two keybytes bruteforcing.

       -X     Disable bruteforce multithreading (SMP only).

       -s     Shows ASCII version of the key at the right of the screen.

       -y     This is an experimental single brute-force attack  which  should
              only  be used when the standard attack mode fails with more than
              one million IVs.

       -z     Uses PTW (Andrei Pyshkin, Erik Tews and  Ralf-Philipp  Weinmann)
              attack (default attack).

       -P <num> or --ptw-debug <num>
              PTW debug: 1 Disable klein, 2 PTW.

       -K     Use KoreK attacks instead of PTW.

       -D or --wep-decloak
              WEP decloak mode.

       -1 or --oneshot
              Run only 1 try to crack key with PTW.

       -M <num>
              Specify maximum number of IVs to use.

       WEP and WPA-PSK cracking options

       -w <words>
              Path  to  a dictionary file for wpa cracking. Specify "-" to use
              stdin.  Here  is  a  list  of  wordlists:   http://www.aircrack-
              ng.org/doku.php?id=faq#where_can_i_find_good_wordlists

       WPA-PSK cracking options:

       -S     WPA cracking speed test.

       -r <database>
              Path to the airolib-ng database. Cannot be used with '-w'.

       Other options:

       -H or --help
              Show help screen

       -u or --cpu-detect
              Provide information on the number of CPUs and MMX/SSE support