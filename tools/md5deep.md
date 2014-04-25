# md5deep

Notes
-------
Computes  the hashes, or message digest, for any number of files while optionally recursively digging through the directory structure. Can also take a list of known hashes and display the filenames of input files whose hashes either do or do not match any of the known hashes.  Errors are reported to standard error. If no FILES are specified, reads from standard input.


Help Text
-------
```
md5deep version 4.2 by Jesse Kornblum and Simson Garfinkel.
$ md5deep [OPTION]... [FILES]...
See the man page or README.txt file or use -hh for the full list of options
-p <size> - piecewise mode. Files are broken into blocks for hashing
-r        - recursive mode. All subdirectories are traversed
-e        - show estimated time remaining for each file
-s        - silent mode. Suppress all error messages
-z        - display file size before hash
-m <file> - enables matching mode. See README/man page
-x <file> - enables negative matching mode. See README/man page
-M and -X are the same as -m and -x but also print hashes of each file
-w        - displays which known file generated a match
-n        - displays known hashes that did not match any input files
-a and -A add a single hash to the positive or negative matching set
-b        - prints only the bare name of files; all path information is omitted
-l        - print relative paths for filenames
-t        - print GMT timestamp (ctime)
-i/I <size> - only process files smaller/larger than SIZE
-v        - display version number and exit
-d        - output in DFXML; -u - Escape Unicode; -W FILE - write to FILE.
-j <num>  - use num threads (default 4)
-Z - triage mode;   -h - help;   -hh - full help


```

Example Usage
-------

Links
-------

