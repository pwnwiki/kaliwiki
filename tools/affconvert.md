# affconvert	

Notes
-------
affconvert is part of the AFF toolset. This program can interconvert between all of the different file formats that AFF supports. It can also be used to restore AFF files on raw disk partitions. [1]

Help Text
-------
```
affconvert version 3.7.1

usage:   affconvert [options] file1 [... files] 

examples:
  affconvert file1.iso --- convert file1.iso to file1.aff
  affconvert file1.iso file2.iso file3.iso...  --- batch convert files
  affconvert -r -e iso image.aff --- convert image.aff to image.iso
  affconvert -M4g -o/media/dvd.afd  bigfile.aff  --- split an AFF file into 4GB chunks for archiving to DVD


General options:
      -q       -- Quiet mode. Don't ask questions, don't print status.

AFF output options:
      -a ext   -- use 'ext' for aff files (default is aff)
                  (use .afd for AFD files)
      -Mn[kgm] -- set maximum size of output file. Suffix with g, m or k.
      -sn      -- set the image_pagesize (default 16777216)
      -x       -- don't compress AFF file.
      -O dir   -- use 'dir' as the output directory
      -o file  -- output to 'file' (can only convert one at a time)
                  File is AFF is file ends .aff; otherwise assumes raw.
      -Xn      -- Set compression to n; default is 7
      -L       -- Use the LZMA compression algorithm (better but slower)

Raw output options:
      -r       -- force raw output. 
      -e ext   -- use 'ext' for the raw files (default raw)
                  (implies -r)

Dangerous input options:
      -z       -- zap; delete the output file if it already exists.
      -Z       -- Do not automatically probe for gzip/bzip2 compression.
      -y       -- Always answer yes/no questions 'yes.'
      -V = Just print the version number and exit.


```

Example Usage
-------
```
affconvert file1.iso --- convert file1.iso to file1.aff
affconvert file1.iso file2.iso file3.iso...  --- batch convert files
affconvert -r -e iso image.aff --- convert image.aff to image.iso
```

Links
-------
[1] http://www.forensicswiki.org/wiki/Afconvert
