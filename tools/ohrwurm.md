# ohrwurm

Notes
-------

Help Text
-------
```
ohrwurm-0.1
enabled kernel routing.

usage: ohrwurm -a <IP target a> -b <IP target b> [-s <randomseed>] [-e <bit error ratio in %>] [-i <interface>] [-A <RTP port a> -B <RTP port b>]

	-a <IPv4 address A in dot-decimal notation> SIP phone A
	-b <IPv4 address B in dot-decimal notation> SIP phone B
	-s <integer> randomseed (default: read from /dev/urandom)
	-e <double> bit error ratio in % (default: 1.230000)
	-i <interfacename> network interface (default: eth0)
	-t suppress RTCP packets (default: dont suppress)
	-A <port number> of RTP port on IP a (requires -B)
	-B <port number> of RTP port on IP b (requires -A)
	   note: using -A and -B skips SIP sniffing, any RTP can be fuzzed

```

Example Usage
-------

Links
-------

