EASSIDE-NG

NAME
       easside-ng  - an auto-magic tool which allows you to communicate via an
       WEP-encrypted AP without knowing the key

SYNOPSIS
       easside-ng <options>

DESCRIPTION
       easside-ng is an auto-magic tool which allows you to communicate via an
       WEP-encrypted  access  point (AP) without knowing the WEP key. It first
       identifies a network, then proceeds to associate with it,  obtain  PRGA
       (pseudo random generation algorithm) xor data, determine the network IP
       scheme and then setup a TAP interface so that you can communicate  with
       the  AP  without  requiring  the WEP key. All this is done without your
       intervention.

OPTIONS
       -h     Shows the help screen.

       -v <victim mac>
              Victim BSSID (Optional).

       -m <src mac>
              Source MAC address to be used (Optional).

       -i <ip>
              Source IP address to be used on the wireless  LAN.  Defaults  to
              the decoded network plus '.123' (Optional).

       -r <router ip>
              IP  address of the AP router. This could be the WAN IP of the AP
              or an actual router IP depending on the  topology.  Defaults  to
              the decoded network plus '.1' (Optional).

       -s <buddy ip>
              IP address of Buddy-ng server (Mandatory)

       -f <iface>
              Wireless interface to use (Mandatory)

       -c <channel>
              Lock interface to this channel (Optional).

       -n     Determine Internet IP only.