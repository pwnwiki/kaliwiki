# blkstat

Notes
-------
blkstat - Display details of a file system data unit (i.e. block or sector)

Help Text
-------
```
usage: blkstat [-vV] [-f fstype] [-i imgtype] [-b dev_sector_size] [-o imgoffset] image [images] addr
	-f fstype: File system type (use '-f list' for supported types)
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-o imgoffset: The offset of the file system in the image (in sectors)
	-v: Verbose output to stderr
	-V: Print version

```

Example Usage
-------

Links
-------
[1] http://www.sleuthkit.org/sleuthkit/man/blkstat.html