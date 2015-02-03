# fragroute

Notes
-------

Help Text
-------
```
Usage: fragroute [-f file] dst
Rules:
       delay first|last|random <ms>
       drop first|last|random <prob-%>
       dup first|last|random <prob-%>
       echo <string> ...
       ip_chaff dup|opt|<ttl>
       ip_frag <size> [old|new]
       ip_opt lsrr|ssrr <ptr> <ip-addr> ...
       ip_ttl <ttl>
       ip_tos <tos>
       order random|reverse
       print
       tcp_chaff cksum|null|paws|rexmit|seq|syn|<ttl>
       tcp_opt mss|wscale <size>
       tcp_seg <size> [old|new]
```

Example Usage
-------

Links
-------
