# icat-sleuthkit

Notes
-------
icat-sleuthkit - Output the contents of a file based on its inode number.

Help Text
-------
```
usage: icat-sleuthkit [-hHsvV] [-f fstype] [-i imgtype] [-b dev_sector_size] [-o imgoffset] image [images] inum[-typ[-id]]
	-h: Do not display holes in sparse files
	-r: Recover deleted file
	-R: Recover deleted file and suppress recovery errors
	-s: Display slack space at end of file
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-f fstype: File system type (use '-f list' for supported types)
	-o imgoffset: The offset of the file system in the image (in sectors)
	-v: verbose to stderr
	-V: Print version

```

Example Usage
-------

Links
-------

