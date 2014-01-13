AIRDECAP-NG

NAME
       airdecap-ng - decrypt a WEP/WPA crypted pcap file

SYNOPSIS
       airdecap-ng [options] <pcap file>

DESCRIPTION
       airdecap-ng  decrypts a WEP/WPA crypted pcap file to a uncrypted one by
       using the right WEP/WPA keys.

OPTIONS
       -H, --help
              Shows the help screen.

       -l     Do not remove the 802.11 header.

       -b <bssid>
              Access point MAC address filter.

       -k <pmk>
              WPA Pairwise Master Key in hex.

       -e <essid>
              Target network SSID. For SSID containing special characters, see
              http://www.aircrack-ng.org/doku.php?id=faq#how_to_use_spaâ€
              ces_double_quote_and_single_quote_etc._in_ap_names

       -p <pass>
              Target network WPA passphrase.

       -w <key>
              Target network WEP key in hex.

EXAMPLES
       airdecap-ng -b 00:09:5B:10:BC:5A open-network.cap
       airdecap-ng -w 11A3E229084349BC25D97E2939 wep.cap
       airdecap-ng -e my_essid -p my_passphrase tkip.cap
