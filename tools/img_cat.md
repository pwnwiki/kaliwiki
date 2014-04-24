# img_cat

Notes
-------
img_cat outputs the contents of an image file. Image files that are not raw will have embedded data and metadata. img_cat will output only the data. This allows you to convert an embedded format to raw or to calculate the MD5 hash of the data by piping the output to the appropriate tool.

Help Text
-------
```
usage: img_cat [-vV] [-i imgtype] [-b dev_sector_size] [-s start_sector] [-e stop_sector] image
	-i imgtype: The format of the image file (use 'i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-s start_sector: The sector number to start at
	-e stop_sector:  The sector number to stop at
	-v: verbose output to stderr
	-V: Print version


```

Example Usage
-------

Links
-------

