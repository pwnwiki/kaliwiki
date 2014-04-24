# tsk_compredir

Notes
-------
tsk_comparedir - compare the contents of a directory with the contents of an image or local device.

Help Text
-------
```
usage: tsk_comparedir [-f fstype] [-i imgtype] [-b dev_sector_size] [-o sector_offset] [-n start_inum] [-vV] image [image] comparison_directory
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-f fstype: The file system type (use '-f list' for supported types)
	-o sector_offset: sector offset for file system to compare
	-n start_inum: inum for directory in image file to start compare at
	-v: verbose output to stderr
	-V: Print version
```

Example Usage
-------
To compare the directories in image.dd to those in directory:
tsk_comparedir ./image.dd ./directory

Links
-------
[1] http://www.sleuthkit.org/sleuthkit/man/tsk_comparedir.html
