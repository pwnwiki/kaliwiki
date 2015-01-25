WESSIDE-NG

NAME
       wesside-ng  - crack a WEP key of an open network without user interven‐
       tion

SYNOPSIS
       wesside-ng <options>

DESCRIPTION
       wesside-ng is an auto-magic tool which incorporates a number  of  tech‐
       niques to seamlessly obtain a WEP key in minutes. It first identifies a
       network, then proceeds to associate with it, obtain PRGA (pseudo random
       generation  algorithm) xor data, determine the network IP scheme, rein‐
       ject ARP requests and finally determine the WEP key. All this  is  done
       without your intervention.

OPTIONS
       -h     Shows the help screen.

       -i <iface>
              Wireless interface name. (Mandatory)

       -n <network ip>
              Network  IP as in 'who has destination IP (netip) tell source IP
              (myip)'. Defaults to the source IP on the ARP request  which  is
              captured and decrypted. (Optional)

       -m <my ip>
              \(aqwho  has  destination  IP (netip) tell source IP (myip)\(aq.
              Defaults  to  the  network.123  on  the  ARP  request   captured
              (Optional).

       -a <source mac>
              Source MAC address (Optional)

       -c     Do not crack the key. Simply capture the packets until control-C
              is hit to stop the program! (Optional)

       -p <min PRGA>
              Determines the minimum number of bytes of PRGA  which  is  gath‐
              ered. Defaults to 128 bytes. (Optional).

       -v <victim MAC>
              Wireless access point MAC address (Optional).

       -t <threshold>
              For  each  number of IVs specified, restart the airecrack-ng PTW
              engine (Optional). It will restart PTW every <threshold> IVs.

       -f <channel>
              Allows the highest channel for scanning to be defined.  Defaults
              to channel 11 (Optional).