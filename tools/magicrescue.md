# magicrescue

Notes
-------
Magic Rescue opens devices for reading, scans them for file types it knows how to recover and calls an external program to extract them. It looks at "magic bytes" in file contents, so it can be used both as an undelete utility and for recovering a corrupted drive or partition.  It works on any file system, but on very fragmented file systems it can only recover the first chunk of each file. These chunks are sometimes as big as 50MB, however.

To invoke magicrescue, you must specify at least one device and the -d and -r options.  See the "USAGE" section in this manual for getting started.


Help Text
-------
```
Usage: magicrescue [-I FILE] [-M MODE] [-O [+-=][0x]OFFSET] [-b BLOCKSIZE]
	-d OUTPUT_DIR -r RECIPE1 [-r RECIPE2 [...]] DEVICE1 [DEVICE2 [...]]

  -b  Only consider files starting at a multiple of BLOCKSIZE.
  -d  Mandatory.  Output directory for found files.
  -r  Mandatory.  Recipe name, file or directory.
  -I  Read input file names from this file ("-" for stdin)
  -M  Produce machine-readable output to stdout.
  -O  Resume from specified offset (hex or decimal) in the first device.


```

Example Usage
-------

Links
-------

