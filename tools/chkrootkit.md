# chkrootkit

Notes
-------
```
chkrootkit is a tool to locally check for signs of a rootkit. It contains:
 * chkrootkit: a shell script that checks system binaries for rootkit modification.
 * ifpromisc.c: checks if the network interface is in promiscuous mode.
 * chklastlog.c: checks for lastlog deletions.
 * chkwtmp.c: checks for wtmp deletions.
 * check_wtmpx.c: checks for wtmpx deletions.  (Solaris only)
 * chkproc.c: checks for signs of LKM trojans.
 * chkdirs.c: checks for signs of LKM trojans.
 * strings.c: quick and dirty strings replacement.
 * chkutmp.c: checks for utmp deletions.
```

Help Text
-------
```
Usage: /usr/sbin/chkrootkit [options] [test ...]
Options:
        -h                show this help and exit
        -V                show version information and exit
        -l                show available tests and exit
        -d                debug
        -q                quiet mode
        -x                expert mode
        -e                exclude known false positive files/dirs, quoted,
                          space separated, READ WARNING IN README
        -r dir            use dir as the root directory
        -p dir1:dir2:dirN path for the external commands used by chkrootkit
        -n                skip NFS mounted dirs
```

Example Usage
-------

Links
-------
Homepage: http://www.chkrootkit.org/
