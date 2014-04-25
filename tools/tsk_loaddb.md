# tsk_loaddb

Notes
-------
tsk_loaddb - populate a SQLite database with metadata from a disk image

Help Text
-------
```
usage: tsk_loaddb [-vVk] [-i imgtype] [-b dev_sector_size] [-d output_dir] image [image]
	-k: Don't create block data table
	-d output_dir: The directory to store the database in (default is the same directory as the image)
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-v: verbose output to stderr
	-V: Print version
```

Example Usage
-------
To load image data from image.dd to image.dd.db:
 tsk_loaddb ./image.dd

Links
-------
[1] http://www.sleuthkit.org/sleuthkit/man/tsk_loaddb.html
