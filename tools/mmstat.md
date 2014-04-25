# mmstat

Notes
-------
mmstat displays the general details of a volume system, which includes partition tables and disk labels. Mainly, the type is given.


Help Text
-------
```
mmstat [-i imgtype] [-b dev_sector_size] [-o imgoffset] [-vV] [-t vstype] image [images]
	-t vstype: The volume system type (use '-t list' for list of supported types)
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

