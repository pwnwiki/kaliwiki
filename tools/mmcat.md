# mmcat

Notes
-------
mmcat outputs the contents of a specific volume to stdout.  This allows you to extract the contents of a partition to a separate file.

Help Text
-------
```
mmcat [-i imgtype] [-b dev_sector_size] [-o imgoffset] [-vV] [-t vstype] image [images] part_num
	-t vstype: The type of partition system (use '-t list' for list of supported types)
	-i imgtype: The format of the image file (use '-i list' for list of supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-o imgoffset: Offset to the start of the volume that contains the partition system (in sectors)
	-v: verbose output
	-V: print the version

```

Example Usage
-------

Links
-------

