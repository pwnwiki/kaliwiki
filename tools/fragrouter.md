# fragrouter

Notes
-------

Help Text
-------
```
Version 1.6
Usage: fragrouter [-i interface] [-p] [-g hop] [-G hopcount] ATTACK

 where ATTACK is one of the following:

 -B1: base-1: normal IP forwarding
 -F1: frag-1: ordered 8-byte IP fragments
 -F2: frag-2: ordered 24-byte IP fragments
 -F3: frag-3: ordered 8-byte IP fragments, one out of order
 -F4: frag-4: ordered 8-byte IP fragments, one duplicate
 -F5: frag-5: out of order 8-byte fragments, one duplicate
 -F6: frag-6: ordered 8-byte fragments, marked last frag first
 -F7: frag-7: ordered 16-byte fragments, fwd-overwriting
 -T1: tcp-1:  3-whs, bad TCP checksum FIN/RST, ordered 1-byte segments
 -T3: tcp-3:  3-whs, ordered 1-byte segments, one duplicate
 -T4: tcp-4:  3-whs, ordered 1-byte segments, one overwriting
 -T5: tcp-5:  3-whs, ordered 2-byte segments, fwd-overwriting
 -T7: tcp-7:  3-whs, ordered 1-byte segments, interleaved null segments
 -T8: tcp-8:  3-whs, ordered 1-byte segments, one out of order
 -T9: tcp-9:  3-whs, out of order 1-byte segments
 -C2: tcbc-2: 3-whs, ordered 1-byte segments, interleaved SYNs
 -C3: tcbc-3: ordered 1-byte null segments, 3-whs, ordered 1-byte segments
 -R1: tcbt-1: 3-whs, RST, 3-whs, ordered 1-byte segments
 -I2: ins-2:  3-whs, ordered 1-byte segments, bad TCP checksums
 -I3: ins-3:  3-whs, ordered 1-byte segments, no ACK set
 -M1: misc-1: Windows NT 4 SP2 - http://www.dataprotect.com/ntfrag/
 -M2: misc-2: Linux IP chains - http://www.dataprotect.com/ipchains/
```

Example Usage
-------

Links
-------
