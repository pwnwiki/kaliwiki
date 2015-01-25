TKIPTUN-NG

NAME
       tkiptun-ng - inject a few frames into a WPA TKIP network with QoS

SYNOPSIS
       tkiptun-ng [options] <replay interface>

DESCRIPTION
       tkiptun-ng is a tool created by Martin Beck aka hirte, a member of air‐
       crack-ng team. This tool is able to inject a few frames into a WPA TKIP
       network with QoS. He worked with Erik Tews (who created PTW attack) for
       a conference in PacSec 2008: "Gone in 900 Seconds, Some  Crypto  Issues
       with WPA".

OPERATION
       -H, --help
              Shows the help screen.

       Filter options:

       -d <dmac>
              MAC address of destination.

       -s <smac>
              MAC address of source.

       -m <len>
              Minimum packet length.

       -n <len>
              Maximum packet length.

       -t <tods>
              Frame control, "To" DS bit.

       -f <fromds>
              Frame control, "From" DS bit.

       -D     Disable AP Detection.

       Replay options:

       -x <nbpps>
              Number of packets per second.

       -p <fctrl>
              Set frame control word (hex).

       -a <bssid>
              Set Access Point MAC address.

       -c <dmac>
              Set destination MAC address.

       -h <smac>
              Set source MAC address.

       -F     Choose first matching packet.

       -e <essid>
              Set target SSID.

       Debug options:

       -K <prga>
              Keystream for continuation.

       -y <file>
              Keystream file for continuation.

       -j     Inject FromFS packets.

       -P <PMK>
              Pairwise  Master  key  (PMK)  for  verification or vulnerability
              testing.

       -p <PSK>
              Preshared key (PSK) to calculate PMK with essid.

       Source options:

       -i <iface>
              Capture packets from this interface.

       -r <file>
              Extract packets from this pcap file.