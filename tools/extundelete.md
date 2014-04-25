# extundelete

Notes
-------
extundelete is a utility that can recover deleted files from an ext3 or ext4 partition.

Help Text
-------
```
Usage: extundelete [options] [--] device-file
Options:
  --version, -[vV]       Print version and exit successfully.
  --help,                Print this help and exit successfully.
  --superblock           Print contents of superblock in addition to the rest.
                         If no action is specified then this option is implied.
  --journal              Show content of journal.
  --after dtime          Only process entries deleted on or after 'dtime'.
  --before dtime         Only process entries deleted before 'dtime'.
Actions:
  --inode ino            Show info on inode 'ino'.
  --block blk            Show info on block 'blk'.
  --restore-inode ino[,ino,...]
                         Restore the file(s) with known inode number 'ino'.
                         The restored files are created in ./RESTORED_FILES
                         with their inode number as extension (ie, file.12345).
  --restore-file 'path'  Will restore file 'path'. 'path' is relative to root
                         of the partition and does not start with a '/' (it
                         must be one of the paths returned by --dump-names).
                         The restored file is created in the current
                         directory as 'RECOVERED_FILES/path'.
  --restore-files 'path' Will restore files which are listed in the file 'path'.
                         Each filename should be in the same format as an option
                         to --restore-file, and there should be one per line.
  --output-dir 'path'    Restore files in the output dir 'path'.
                         By default the restored files are created under current directory 'RECOVERED_FILES'.
  --restore-all          Attempts to restore everything.
  -j journal             Reads an external journal from the named file.
  -b blocknumber         Uses the backup superblock at blocknumber when opening
                         the file system.
  -B blocksize           Uses blocksize as the block size when opening the file
                         system.  The number should be the number of bytes.

```

Example Usage
-------
extundelete is designed to undelete files from an unmounted partition to a separate (mounted) partition. extundelete will restore any files it finds to a subdirectory of the current directory named “RECOVERED_FILES”. To run the program, type “extundelete --help” to see various options available to you.

Typical usage to restore all deleted files from a partition looks like this:
$ extundelete /dev/sda4 --restore-all

Links
-------
http://extundelete.sourceforge.net/
