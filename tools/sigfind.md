# sigfind

Notes
-------
sigfind searches through a file and looks for the hex_signature at a given offset.  This can be used to search for lost boot sectors, superblocks, and partition tables.

Help Text
-------
```
sigfind [-b bsize] [-o offset] [-t template] [-lV] [hex_signature] file
	-b bsize: Give block size (default 512)
	-o offset: Give offset into block where signature should exist (default 0)
	-l: Signature will be little endian in image
	-V: Version
	-t template: The name of a data structure template:
		dospart, ext2, ext3, fat, hfs, hfs+, ntfs, ufs1, ufs2

```

Example Usage
-------
```
sigfind -o 510 -l AA55 disk.dd
sigfind -t fat disk.dd
```

Links
-------
[1] http://www.sleuthkit.org/sleuthkit/man/sigfind.html
