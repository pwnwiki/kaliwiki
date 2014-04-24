# blkcat

Notes
-------
blkcat displays num data units (default is one) starting at the unit address unit_addr from image to stdout in different formats (default is raw). blkcat was called dcat in TSK versions prior to 3.0.0.


Help Text
-------
```
usage: blkcat [-ahsvVw] [-f fstype] [-i imgtype] [-b dev_sector_size] [-o imgoffset] [-u usize] image [images] unit_addr [num]
	-a: displays in all ASCII 
	-h: displays in hexdump-like fashion
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-o imgoffset: The offset of the file system in the image (in sectors)
	-f fstype: File system type (use '-f list' for supported types)
	-s: display basic block stats such as unit size, fragments, etc.
	-v: verbose output to stderr
	-V: display version
	-w: displays in web-like (html) fashion
	-u usize: size of each data unit in image (for raw, blkls, swap)
	[num] is the number of data units to display (default is 1)


```

Example Usage
-------
```
 # blkcat -hw image 264 4
```
or 
```
 # blkcat -hw image 264
```

Links
-------

