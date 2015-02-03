# ddrescue

Notes
-------
dd_rescue copies data from one file (or block device) to another.

Help Text
-------
```
dd_rescue Version 1.28, garloff@suse.de, GNU GPL
 ($Id: dd_rescue.c,v 1.130 2012/05/19 20:46:14 garloff Exp $)
 (compiled Dec 15 2012 12:04:22 by gcc (Debian 4.7.2-4) 4.7.2)
 (features: O_DIRECT splice )
dd_rescue copies data from one file (or block device) to another.
USAGE: dd_rescue [options] infile outfile
Options: -s ipos    start position in  input file (default=0),
         -S opos    start position in output file (def=ipos),
         -b softbs  block size for copy operation (def=65536, 1048576 for -d),
         -B hardbs  fallback block size in case of errs (def=4096, 512 for -d),
         -e maxerr  exit after maxerr errors (def=0=infinite),
         -m maxxfer maximum amount of data to be transfered (def=0=inf),
         -y syncfrq frequency of fsync calls on outfile (def=512*softbs),
         -l logfile name of a file to log errors and summary to (def=""),
         -o bbfile  name of a file to log bad blocks numbers (def=""),
         -r         reverse direction copy (def=forward),
         -t         truncate output file (def=no),
         -d/D       use O_DIRECT for input/output (def=no),
         -k         use efficient in-kernel zerocopy splice
         -w         abort on Write errors (def=no),
         -a         spArse file writing (def=no),
         -A         Always write blocks, zeroed if err (def=no),
         -i         interactive: ask before overwriting data (def=no),
         -f         force: skip some sanity checks (def=no),
         -p         preserve: preserve ownership / perms (def=no),
         -q         quiet operation,
         -v         verbose operation,
         -V         display version and exit,
         -h         display this help and exit.
Sizes may be given in units b(=512), k(=1024), M(=1024^2) or G(1024^3) bytes
This program is useful to rescue data in case of I/O errors, because
 it does not necessarily abort or truncate the output.


```

Example Usage
-------

Links
-------

