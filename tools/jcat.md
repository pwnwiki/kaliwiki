# jcat

Notes
-------
jcat - Show the contents of a block in the file system journal.

Help Text
-------
```
usage: jcat [-f fstype] [-i imgtype] [-b dev_sector_size] [-o imgoffset] [-vV] image [images] [inode] blk
	blk: The journal block to view
	inode: The file system inode where the journal is located
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-f fstype: File system type (use '-f list' for supported types)
	-o imgoffset: The offset of the file system in the image (in sectors)
	-v: verbose output to stderr
	-V: print version

```

Example Usage
-------
jcat -f linux-ext3 img.dd 34 | xxd

Links
-------

