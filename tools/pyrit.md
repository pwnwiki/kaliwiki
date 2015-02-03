# pyrit

Notes
-------
Pyrit allows to create massive databases, pre-computing part of the IEEE 802.11 WPA/WPA2-PSK authentication phase in a space-time-tradeoff. Exploiting the computational power of Many-Core- and other platforms through ATI-Stream, Nvidia CUDA and OpenCL, it is currently by far the most powerful attack against one of the world's most used security-protocols.[1]


Help Text
-------
```
Pyrit 0.4.0 (C) 2008-2011 Lukas Lueg http://pyrit.googlecode.com
This code is distributed under the GNU General Public License v3+

Usage: pyrit [options] command

Recognized options:
  -b               : Filters AccessPoint by BSSID
  -e               : Filters AccessPoint by ESSID
  -h               : Print help for a certain command
  -i               : Filename for input ('-' is stdin)
  -o               : Filename for output ('-' is stdout)
  -r               : Packet capture source in pcap-format
  -u               : URL of the storage-system to use
  --all-handshakes : Use all handshakes instead of the best one

Recognized commands:
  analyze                 : Analyze a packet-capture file
  attack_batch            : Attack a handshake with PMKs/passwords from the db
  attack_cowpatty         : Attack a handshake with PMKs from a cowpatty-file
  attack_db               : Attack a handshake with PMKs from the db
  attack_passthrough      : Attack a handshake with passwords from a file
  batch                   : Batchprocess the database
  benchmark               : Determine performance of available cores
  benchmark_long          : Longer and more accurate version of benchmark (~10 minutes)
  check_db                : Check the database for errors
  create_essid            : Create a new ESSID
  delete_essid            : Delete a ESSID from the database
  eval                    : Count the available passwords and matching results
  export_cowpatty         : Export results to a new cowpatty file
  export_hashdb           : Export results to an airolib database
  export_passwords        : Export passwords to a file
  help                    : Print general help
  import_passwords        : Import passwords from a file-like source
  import_unique_passwords : Import unique passwords from a file-like source
  list_cores              : List available cores
  list_essids             : List all ESSIDs but don't count matching results
  passthrough             : Compute PMKs and write results to a file
  relay                   : Relay a storage-url via RPC
  selftest                : Test hardware to ensure it computes correct results
  serve                   : Serve local hardware to other Pyrit clients
  strip                   : Strip packet-capture files to the relevant packets
  stripLive               : Capture relevant packets from a live capture-source
  verify                  : Verify 10% of the results by recomputation

```

Example Usage[2]
-------
### First steps with capture-files and wordlists
Pyrit can understand packet capture files in pcap-format. These files basically contain what was captured from the air. Our first meaningful step in this tutorial is to let Pyrit analyze one of the capture files and give us some information about the content.

### Analyzing a capture file
Issue to following command to analyze the file wpapsk-linksys.dump.gz:

```
pyrit -r wpapsk-linksys.dump.gz analyze
```

Pyrit should answer with output very similar like the following:

```
Pyrit 0.3.0 (C) 2008-2010 Lukas Lueg http://pyrit.googlecode.com
This code is distributed under the GNU General Public License v3+

Parsing file 'wpapsk-linksys.dump.gz' (1/1)...
587 packets (587 802.11-packets), 1 APs

#1: AccessPoint 00:0b:86:c2:a4:85 ('linksys')
  #0: Station 00:13:ce:55:98:ef, handshake found
  #1: Station 01:00:5e:7f:ff:fa
  #2: Station 01:00:5e:00:00:16
```

Pyrit has successfuly parsed the capture file and found one AccessPoint with BSSID 00:0b:86:c2:a4:85 and ESSID 'linksys' and three Stations communicating with that AccessPoint. The key-negotiation (known as the fourway-handshake) between the Station with MAC 00:13:ce:55:98:ef and the AccessPoint has also been recorded in the capture file. We can use the data from this handshake to guess that password that is used to protect the network.

Please note that Pyrit can transparently read/write gzip-compressed files; this becomes very handy when dealing with large wordlists or cowpatty-files that may take hundrets of megabytes.

### Attacking a handshake and revealing the password
We now use the example wordlist dict.gz and let Pyrit guess the password that was used in the key-negotiation between AccessPoint 00:0b:86:c2:a4:85 and Station 00:13:ce:55:98:ef. The correct password should get detected, if it is part of the list. In our terms, this is known as a "passthrough-attack". Issue the following command:

```
pyrit -r wpapsk-linksys.dump.gz -i dict.gz -b 00:0b:86:c2:a4:85 attack_passthrough
```

This tells Pyrit to take the capture-file wpapsk-linksys.dump.gz and attack the key-negotiation with AccessPoint 00:0b:86:c2:a4:85 using the dictionary-file dict.gz.

Please note that you do not always have to tell Pyrit which AccessPoint to choose from the capture-file - Pyrit will usually be able to figure that out by itself.

You should get a response very similar to the following:

```
Pyrit 0.3.0 (C) 2008-2010 Lukas Lueg http://pyrit.googlecode.com
This code is distributed under the GNU General Public License v3+

Parsing file 'wpapsk-linksys.dump.gz' (1/1)...
587 packets (587 802.11-packets), 1 APs

Tried 4091 PMKs so far; 935 PMKs per second.

The password is 'dictionary'.
```

We've successfully revealed that the password used to protect the network 00:0b:86:c2:a4:85 is "dictionary"...

### Interlude: Stripping a capture-file from unnecessary cruft
Capture-files are usually simple dumps of the traffic captured directly from the air. For our purpose, we are only interested in a very tiny fraction of the traffic between AccessPoint and Station. Pyrit can help reducing the size of a packet-capture file by analyzing the traffic and throwing away all packets that are of no use for us. We end up with a new, very small capture file that still holds all valuable information and is useable with other tools like Wireshark.

Please note that stripping a capture file is not necessary. It's sole purpose is to make life a little easier when it comes to large capture files.

Our original example has 587 packets and a size of roughly 13kb. Issue the following command:
```

pyrit -r wpapsk-linksys.dump.gz -o wpapsk-linksys_stripped.dump.gz strip
```

You should get a response like the following:
```

Pyrit 0.3.0 (C) 2008-2010 Lukas Lueg http://pyrit.googlecode.com
This code is distributed under the GNU General Public License v3+

Parsing file 'wpapsk-linksys.dump.gz' (1/1)...
587 packets (587 802.11-packets), 1 APs

#1: AccessPoint 00:0b:86:c2:a4:85 ('linksys')
  #0: Station 00:13:ce:55:98:ef (1 authentications)

New pcap-file 'wpapsk-linksys_stripped.dump.gz' written (4 out of 587 packets)
```

The new capture file wpapsk-linksys_stripped.dump.gz has a size of only a few hundred bytes and contains only three from the key-negotiation (used to attack the password) and one beacon-frame (used to detect the network's ESSID).


Links
-------
1. [Google Code Page](https://code.google.com/p/pyrit/)
2. [Tutorial](https://code.google.com/p/pyrit/wiki/Tutorial)
