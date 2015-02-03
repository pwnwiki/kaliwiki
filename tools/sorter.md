# sorter

Notes
-------
sorter is a Perl script that analyzes a file system to organize the allocated and unallocated files by file type. It runs the 'file' command on each file and organizes the files according to the rules in configuration files. Extension mismatching is also done to identify 'hidden' files. One can also provide hash databases for files that are known to be good and can be ignored and files that are known to be bad and should be alerted.

By default, the program uses the configuration files in the directory where The Sleuth Kit was installed. Those can be overruled with run-time options. There is a standard configuration file for all file system types and then a specific one for a given operating system.


Help Text
-------
```
sorter [-b size] [-E] [-e] [-h]  [-l] [-md5] [-s] [-sha1] [-U] [-v] [-V] [-a hash_alert] [-c config] [-C config] [-d dir] [-m mnt] [-n nsrl_db] [-x hash_exclude] [-o imgoffset] [-f fstype] [-i imgtype] image [images] [dir_meta_addr] 

    -b size: Minimum size.  Ignore files smaller than 'size'
	-E: Perform category indexing only (no extension checks - was '-i')
	-e: Perform extension checks only (no category index files)
	-h: HTML Format
	-l: List index to STDOUT (no files are ever written)
	-md5: Print the MD5 value with the index output
	-s: Save files to category directories
	-sha1: Print the SHA-1 value with the index output
	-U: Ignore the unknown category - only save catgories in config files
	-v: verbose debugging output
	-V: print version information
	-a hash_alert: hash database of hashes to alert on
	-c config: specify a config file to use (in addition to default files)
	   NOTE: This config file has priority over default files
	-C config: specify the ONLY config file to use
	-d dir: Save category index files in the specified directory
	-f fstype: file system type (Sleuth Kit types) of image
	-i imgtype: Format of image file
	-o imgoffset: Offset of file system in image (in sectors)
	-m mnt: The mounting point of the image
	-n nsrl_db: The NIST NSRL database file (NSRLFile.txt) (hashes to ignore)
	-x hash_exclude: hash database of hashes to ignore
	dir_meta_addr: Address of directory to start analyzing from 
	image: image to analyze

```

Example Usage
-------
To run sorter with no hash databases, the following can be used:
```
 sorter -f ntfs -d data/sorter images/hda1.dd
 sorter -d data/sorter images/hda1.dd
 sorter -i raw -f ntfs -o 63 -d data/sorter images/hda.dd
```

To include the NSRL, an exclude, and an alert hash database:
```
 sorter -f ntfs -d data/sorter -a /usr/hash/rootkit.db        -x /usr/hash/win2k.db -n /usr/hash/nsrl/NSRLFile.txt        images/hda1.dd
```

To just identify images using the supplied 'images.sort' file:
``` 
 sorter -f ntfs -C /usr/local/sleuthkit/share/sort/images.sort     -d data/sorter -h -s images/hda1.dd
```

Links
-------
[1] http://www.sleuthkit.org/sleuthkit/man/sorter.html
