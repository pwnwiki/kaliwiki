# istat

Notes
-------
istat - Information about an inode number

Help Text
-------
```
usage: istat [-B num] [-f fstype] [-i imgtype] [-b dev_sector_size] [-o imgoffset] [-z zone] [-s seconds] [-vV] image inum
	-B num: force the display of NUM address of block pointers
	-z zone: time zone of original machine (i.e. EST5EDT or GMT)
	-s seconds: Time skew of original machine (in seconds)
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-f fstype: File system type (use '-f list' for supported types)
	-o imgoffset: The offset of the file system in the image (in sectors)
	-v: verbose output to stderr
	-V: print version

```

Example Usage
-------

Links
-------

