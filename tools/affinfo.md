# affinfo 

Notes
-------
affinfo — prints details about the segments

Help Text
-------
```
afinfo version 3.7.1
usage: afinfo [options] infile
   -a = print ALL segments (normally data segments are suppressed)
   -b = print how many bad blocks in each segment (implies -a)
   -i = identify the files, don't do info on them.
   -w = wide output; print more than 1 line if necessary.
   -s segment =   Just print information about 'segment'.
                    (may be repeated)
   -m = validate MD5 hash of entire image
   -S = validate SHA1 hash of entire image
   -v = validate the hash of each page (if present)
   -y = don't print segments of lengths 16 and 20 as hex)
   -p<passphrase> = Specify <passphrase> to decrypt file
   -l = Just print the segment names and exit
   -V = Just print the version number and exit.

Preview Options:
   -X = no data preview; just print the segment names
   -x = print binary values in hex (default is ASCII)

Misc:
   -d = debug
   -A = if infile is a device, print the number of sectors
        and sector size to stdout in XML. Otherwise error

Compilation:
    LZMA compression: Enabled
    QEMU enabled
    FUSE enabled
    Amazon S3 enabled
    HAVE_LIBEXPAT 

```

Example Usage
-------

Links
-------

