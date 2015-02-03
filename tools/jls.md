# jls

Notes
-------
jls  lists  the  records  and entries in a file system journal.  If inode is given, then it will look there for a journal.  Otherwise, it will use the default location.  The output lists the journal block number and a description.


Help Text
-------
```
usage: jls [-f fstype] [-i imgtype] [-b dev_sector_size] [-o imgoffset] [-vV] image [inode]
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-f fstype: File system type (use '-f list' for supported types)
	-o imgoffset: The offset of the file system in the image (in sectors)
	-v: verbose output to stderr
	-V: print version


```

Example Usage
-------
```
jls -f linux-ext3 img.dd
```

Links
-------

