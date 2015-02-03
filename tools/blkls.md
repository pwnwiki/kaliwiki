# blkls

Notes
-------
blkls  opens  the  named image(s) and copies file system data units (blocks).  By default, blkls copies the contents of unallocated data blocks.  blkls was called dls in TSK versions prior to 3.0.0. blkls was called unrm in TCT.


Help Text
-------
```
usage: blkls [-aAelvV] [-f fstype] [-i imgtype] [-b dev_sector_size] [-o imgoffset] image [images] [start-stop]
	-e: every block (including file system metadata blocks)
	-l: print details in time machine list format
	-a: Display allocated blocks
	-A: Display unallocated blocks
	-f fstype: File system type (use '-f list' for supported types)
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-o imgoffset: The offset of the file system in the image (in sectors)
	-s: print slack space only (other flags are ignored
	-v: verbose to stderr
	-V: print version


```

Example Usage
-------

Links
-------

