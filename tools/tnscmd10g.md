# tnscmd10g

Notes
-------

Help Text
-------
```
usage: /usr/bin/tnscmd10g [command] -h hostname
       where 'command' is something like ping, version, status, etc.  
       (default is ping)
       [-p port] - alternate TCP port to use (default is 1521)
       [--logfile logfile] - write raw packets to specified logfile
       [--indent] - indent & outdent on parens
       [--10G] - make it work against 10G
       [--rawcmd command] - build your own CONNECT_DATA string
       [--cmdsize bytes] - fake TNS command size (reveals packet leakage)

```

Example Usage
-------

Links
-------

