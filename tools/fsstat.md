# fsstat

Notes
-------
fsstat - Display general details of a file system image

Help Text
-------
```
usage: fsstat [-tvV] [-f fstype] [-i imgtype] [-b dev_sector_size] [-o imgoffset] image
	-t: display type only
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-f fstype: File system type (use '-f list' for supported types)
	-o imgoffset: The offset of the file system in the image (in sectors)
	-v: verbose output to stderr
	-V: Print version
```

Example Usage
-------
Example from wiki.sleuthkit.org [2]
```
    # fsstat images/hda1.dd
    FILE SYSTEM INFORMATION
    --------------------------------------------
    File System Type: EXT3FS
	<...>

    Group: 0:
      Inode Range: 1 - 15392
      Block Range: 0 - 32767
        Super Block: 0 - 0
        Group Descriptor Table: 1 - 1
        Data bitmap: 2 - 2
        Inode bitmap: 3 - 3
        Inode Table: 4 - 484
        Data Blocks: 485 - 32767

    Group: 1:
      Inode Range: 15393 - 30784
      Block Range: 32768 - 65535
        Super Block: 32768 - 32768
        Group Descriptor Table: 32769 - 32769
        Data bitmap: 32770 - 32770
        Inode bitmap: 32771 - 32771
        Inode Table: 32772 - 33252
        Data Blocks: 33253 - 65535

    Group: 2:
      Inode Range: 30785 - 46176
      Block Range: 65536 - 98303
        Data bitmap: 65536 - 65536
        Inode bitmap: 65537 - 65537
        Inode Table: 65540 - 66020
        Data Blocks: 65538 - 65539, 66021 - 98303

    <...>
```

Links
-------
[1] http://www.sleuthkit.org/sleuthkit/man/fsstat.html
[2] http://wiki.sleuthkit.org/index.php?title=FS_Analysis
