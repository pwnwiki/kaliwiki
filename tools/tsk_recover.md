# tsk_recover

Notes
-------
tsk_recover recover files to the output_dir from the image.  By default recovers only unallocated files. With flags, it will export all files.

Help Text
-------
```
usage: tsk_recover [-vVae] [-f fstype] [-i imgtype] [-b dev_sector_size] [-o sector_offset] [-d dir_inum] image [image] output_dir
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-f fstype: The file system type (use '-f list' for supported types)
	-v: verbose output to stderr
	-V: Print version
	-a: Recover allocated files only
	-e: Recover all files (allocated and unallocated)
	-o sector_offset: sector offset for a volume to recover (recovers only that volume)
	-d dir_inum: Directory inum to recover from (must also specify a specific partition using -o or there must not be a volume system)

```

Example Usage
-------
To recover only unallocated files from image.dd to the recovered directory:
```
 # tsk_recover ./recovered ./image.dd
```

Links
-------

