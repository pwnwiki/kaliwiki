# hfind.md

Notes
-------
hfind - Lookup a hash value in a hash database

Help Text
-------
```
usage: hfind [-eqV] [-f lookup_file] [-i db_type] db_file [hashes]
	-e: Extended mode - where values other than just the name are printed
	-q: Quick mode - where a 1 is printed if it is found, else 0
	-V: Print version to STDOUT
	-f lookup_file: File with one hash per line to lookup
	-i db_type: Create index file for a given hash database type
	db_file: The location of the original hash database
	[hashes]: hashes to lookup (STDIN is used otherwise)

	Supported types: nsrl-md5, nsrl-sha1, md5sum, hk
```

Example Usage
-------
```
To create an MD5 index file for NIST NSRL:
   * hfind -i nsrl-md5 /usr/local/hash/nsrl/NSRLFile.txt

To lookup a value in the NSRL:
   * hfind /usr/local/hash/nsrl/NSRLFile.txt 76b1f4de1522c20b67acc132937cf82e
   76b1f4de1522c20b67acc132937cf82e Hash Not Found

You can even do both SHA-1 and MD5 if you want:
   * hfind -i nsrl-sha1 /usr/local/hash/nsrl/NSRLFile.txt
   * hfind /usr/local/hash/nsrl/NSRLFile.txt
   76b1f4de1522c20b67acc132937cf82e
   80001A80B3F1B80076B297CEE8805AAA04E1B5BA
   76b1f4de1522c20b67acc132937cf82e Hash Not Found
   80001A80B3F1B80076B297CEE8805AAA04E1B5BA thrdcore.cpp

To make a database of critical binaries of a trusted system, use ’md5sum’:
   * md5sum /bin/* /sbin/* /usr/bin/* /usr/bin/* /usr/local/bin/* /usr/local/sbin/* > system.md5
   * hfind -i md5sum system.md5

To look entries up, the following will work:
   * hfind system.md5 76b1f4de1522c20b67acc132937cf82e
   76b1f4de1522c20b67acc132937cf82e Hash Not Found

or
   * md5sum -q /bin/* | hfind system.md5
   928682269cd3edb1acdf9a7f7e606ff2 /bin/bash
   <...>

or
   * md5sum -q /bin/* > bin.md5
   * hfind -f bin.md5 system.md5
   928682269cd3edb1acdf9a7f7e606ff2 /bin/bash
   <...>
```

Links
-------
[1] http://www.sleuthkit.org/sleuthkit/man/hfind.html
