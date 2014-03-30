# dnmap-server

Notes
-------

Help Text
-------
```
+----------------------------------------------------------------------+
| dnmap_server Version 0.6                                             |
| This program is free software; you can redistribute it and/or modify |
| it under the terms of the GNU General Public License as published by |
| the Free Software Foundation; either version 2 of the License, or    |
| (at your option) any later version.                                  |
|                                                                      |
| Author: Garcia Sebastian, eldraco@gmail.com                          |
| www.mateslab.com.ar                                                  |
+----------------------------------------------------------------------+

usage: /usr/bin/dnmap_server <options>
options:
  -f, --nmap-commands        Nmap commands file
  -p, --port        TCP port where we listen for connections.
  -L, --log-file        Log file. Defaults to /var/log/dnmap_server.conf.
  -l, --log-level       Log level. Defaults to info.
  -v, --verbose_level         Verbose level. Give a number between 1 and 5. Defaults to 1. Level 0 means be quiet.
  -t, --client-timeout         How many time should we wait before marking a client Offline. We still remember its values just in case it cames back.
  -s, --sort         	Field to sort the statical value. You can choose from: Alias, #Commands, UpTime, RunCmdXMin, AvrCmdXMin, Status
  -P, --pem-file         pem file to use for TLS connection. By default we use the server.pem file provided with the server in the current directory.

dnmap_server uses a '<nmap-commands-file-name>.dnmaptrace' file to know where it must continue reading the nmap commands file. If you want to start over again,
just delete the '<nmap-commands-file-name>.dnmaptrace' file
```

Example Usage
-------

Links
-------
