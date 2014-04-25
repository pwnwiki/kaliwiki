# binwalk

Notes
-------
Binwalk is a firmware analysis tool designed to assist in the analysis, extraction, and reverse engineering of firmware images and other binary blobs.

Help Text
-------
```
Binwalk v1.2.2-1
Craig Heffner, http://www.devttys0.com

Usage: binwalk [OPTIONS] [FILE1] [FILE2] [FILE3] ...

Signature Analysis:
	-B, --binwalk                 Perform a file signature scan (default)
	-R, --raw-bytes=<string>      Search for a custom signature
	-A, --opcodes                 Scan for executable code signatures
	-C, --cast                    Cast file contents as various data types
	-m, --magic=<file>            Specify an alternate magic file to use
	-x, --exclude=<filter>        Exclude matches that have <filter> in their description
	-y, --include=<filter>        Only search for matches that have <filter> in their description
	-I, --show-invalid            Show results marked as invalid
	-T, --ignore-time-skew        Do not show results that have timestamps more than 1 year in the future
	-k, --keep-going              Show all matching results at a given offset, not just the first one
	-b, --dumb                    Disable smart signature keywords

Strings Analysis:
	-S, --strings                 Scan for ASCII strings (may be combined with -B, -R, -A, or -E)
	-s, --strlen=<n>              Set the minimum string length to search for (default: 3)

Entropy Analysis:
	-E, --entropy                 Plot file entropy (may be combined with -B, -R, -A, or -S)
	-H, --heuristic               Identify unknown compression/encryption based on entropy heuristics (implies -E)
	-K, --block=<int>             Set the block size for entropy analysis (default: 1024)
	-a, --gzip                    Use gzip compression ratios to measure entropy
	-N, --no-plot                 Do not generate an entropy plot graph
	-F, --marker=<offset:name>    Add a marker to the entropy plot graph
	-Q, --no-legend               Omit the legend from the entropy plot graph
	-J, --save-plot               Save plot as an SVG (implied if multiple files are specified)

Binary Diffing:
	-W, --diff                    Hexdump / diff the specified files
	-K, --block=<int>             Number of bytes to display per line (default: 16)
	-G, --green                   Only show hex dump lines that contain bytes which were the same in all files
	-i, --red                     Only show hex dump lines that contain bytes which were different in all files
	-U, --blue                    Only show hex dump lines that contain bytes which were different in some files
	-w, --terse                   Diff all files, but only display a hex dump of the first file

Extraction Options:
	-D, --dd=<type:ext[:cmd]>     Extract <type> signatures, give the files an extension of <ext>, and execute <cmd>
	-e, --extract=[file]          Automatically extract known file types; load rules from file, if specified
	-M, --matryoshka              Recursively scan extracted files, up to 8 levels deep
	-r, --rm                      Cleanup extracted files and zero-size files
	-d, --delay                   Delay file extraction for files with known footers

Plugin Options:
	-X, --disable-plugin=<name>   Disable a plugin by name
	-Y, --enable-plugin=<name>    Enable a plugin by name
	-p, --disable-plugins         Do not load any binwalk plugins
	-L, --list-plugins            List all user and system plugins by name

General Options:
	-o, --offset=<int>            Start scan at this file offset
	-l, --length=<int>            Number of bytes to scan
	-g, --grep=<text>             Grep results for the specified text
	-f, --file=<file>             Log results to file
	-c, --csv                     Log results to file in csv format
	-O, --skip-unopened           Ignore file open errors and process only the files that can be opened
	-t, --term                    Format output to fit the terminal window
	-q, --quiet                   Supress output to stdout
	-v, --verbose                 Be verbose (specify twice for very verbose)
	-u, --update                  Update magic signature files
	-?, --examples                Show example usage
	-h, --help                    Show help output

```

Example Usage
-------

Links
-------
[1] https://github.com/devttys0/binwalk
[2] http://binwalk.org/
