# fls

Notes
-------
Create a file listing of an image

Help Text
-------
```
usage: fls [-adDFlpruvV] [-f fstype] [-i imgtype] [-b dev_sector_size] [-m dir/] [-o imgoffset] [-z ZONE] [-s seconds] image [images] [inode]
	If [inode] is not given, the root directory is used
	-a: Display "." and ".." entries
	-d: Display deleted entries only
	-D: Display only directories
	-F: Display only files
	-l: Display long version (like ls -l)
	-i imgtype: Format of image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-f fstype: File system type (use '-f list' for supported types)
	-m: Display output in mactime input format with
	      dir/ as the actual mount point of the image
	-o imgoffset: Offset into image file (in sectors)
	-p: Display full path for each file
	-r: Recurse on directory entries
	-u: Display undeleted entries only
	-v: verbose output to stderr
	-V: Print version
	-z: Time zone of original machine (i.e. EST5EDT or GMT) (only useful with -l)
	-s seconds: Time skew of original machine (in seconds) (only useful with -l & -m)

```

Example Usage
-------

Links
-------

