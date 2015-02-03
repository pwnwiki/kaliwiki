# blkcalc

Notes
-------
blkcalc - Converts between unallocated disk unit numbers and regular disk unit numbers.

Help Text
-------
```
usage: blkcalc [-dsu unit_addr] [-vV] [-f fstype] [-i imgtype] [-b dev_sector_size] [-o imgoffset] image [images]
Slowly calculates the opposite block number
	One of the following must be given:
	  -d: The given address is from a 'dd' image 
	  -s: The given address is from a 'blkls -s' (slack) image
	  -u: The given address is from a 'blkls' (unallocated) image
	-f fstype: The file system type (use '-f list' for supported types)
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-o imgoffset: The offset of the file system in the image (in sectors)
	-v: verbose output to stderr
	-V: Print version

```

Example Usage
-------
blkcalc -u 64 images/wd0e

Links
-------
[1] http://www.sleuthkit.org/sleuthkit/man/blkcalc.html
