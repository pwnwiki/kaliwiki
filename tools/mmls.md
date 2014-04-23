# mmls

Notes
-------
mmls displays the layout of the partitions in a volume system, which include partition tables and disk labels.

Help Text
-------
```
mmls [-i imgtype] [-b dev_sector_size] [-o imgoffset] [-BrvV] [-aAmM] [-t vstype] image [images]
	-t vstype: The type of volume system (use '-t list' for list of supported types)
	-i imgtype: The format of the image file (use '-i list' for list supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-o imgoffset: Offset to the start of the volume that contains the partition system (in sectors)
	-B: print the rounded length in bytes
	-r: recurse and look for other partition tables in partitions (DOS Only)
	-v: verbose output
	-V: print the version
Unless any of these are specified, all volume types are shown
	-a: Show allocated volumes
	-A: Show unallocated volumes
	-m: Show metadata volumes
	-M: Hide metadata volumes


```

Example Usage
-------
To list the partition table of a Windows system using autodetect:
```
 # mmls disk_image.dd
```

To list the contents of a BSD system that starts in sector 12345 of a split image:
```
 # mmls -t bsd -o 12345 -i split disk-1.dd disk-2.dd
```

Links
-------

