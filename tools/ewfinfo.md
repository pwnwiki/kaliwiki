# ewfinfo

Notes
-------
ewfinfo is a utility to show meta data stored in EWF files.
ewfinfo is part of the libewf package.  libewf is a library to access the Expert Witness Compression Format (EWF).


Help Text
-------
```
ewfinfo 20130416

Use ewfinfo to determine information about the EWF format (Expert Witness
Compression Format).

Usage: ewfinfo [ -A codepage ] [ -d date_format ] [ -f format ]
               [ -ehimvVx ] ewf_files

	ewf_files: the first or the entire set of EWF segment files

	-A:        codepage of header section, options: ascii (default),
	           windows-874, windows-932, windows-936, windows-949,
	           windows-950, windows-1250, windows-1251, windows-1252,
	           windows-1253, windows-1254, windows-1255, windows-1256,
	           windows-1257 or windows-1258
	-d:        specify the date format, options: ctime (default),
	           dm (day/month), md (month/day), iso8601
	-e:        only show EWF read error information
	-f:        specify the output format, options: text (default),
	           dfxml
	-h:        shows this help
	-i:        only show EWF acquiry information
	-m:        only show EWF media information
	-v:        verbose output to stderr
	-V:        print version


```

Example Usage
-------

Links
-------

