# bulk_extractor

Notes
-------
bulk_extractor is a computer forensics tool that scans a disk image, a file, or a directory of files and extracts useful information without parsing the file system or file system structures.

Help Text
-------
`bulk_extractor version 1.3 $Rev: 10606 $
Usage: bulk_extractor [options] imagefile
  runs bulk extractor and outputs to stdout a summary of what was found where

Required parameters:
   imagefile     - the file to extract
 or  -R filedir  - recurse through a directory of files
                  SUPPORT FOR E01 FILES COMPILED IN
                  SUPPORT FOR AFF FILES COMPILED IN
   -o outdir    - specifies output directory. Must not exist.
                  bulk_extractor creates this directory.
Options:
   -b banner.txt- Add banner.txt contents to the top of every output file.
   -r alert_list.txt  - a file containing the alert list of features to alert
                       (can be a feature file or a list of globs)
                       (can be repeated.)
   -w stop_list.txt   - a file containing the stop list of features (white list
                       (can be a feature file or a list of globs)s
                       (can be repeated.)
   -F <rfile>   - Read a list of regular expressions from <rfile> to find
   -f <regex>   - find occurrences of <regex>; may be repeated.
                  results go into find.txt
   -q nn        - Quiet Rate; only print every nn status reports. Default 0; -1 for no status at all

Tuning parameters:
   -C NN         - specifies the size of the context window (default 16)
   -G NN         - specify the page size (default 16777216)
   -g NN         - specify margin (default 4194304)
   -W n1:n2      - Specifies minimum and maximum word size
                  (default is -w6:14)
   -B NN         - Specify the blocksize for bulk data analysis (default 512)
   -j NN         - Number of analysis threads to run (default 4)
   -M nn        - sets max recursion depth (default 5)

Path Processing Mode:
   -p <path>/f  - print the value of <path> with a given format.
                  formats: r = raw; h = hex.
                  Specify -p - for interactive mode.
                  Specify -p -http for HTTP mode.

Parallelizing:
   -Y <o1>      - Start processing at o1 (o1 may be 1, 1K, 1M or 1G)
   -Y <o1>-<o2> - Process o1-o2
   -A <off>     - Add <off> to all reported feature offsets

Debugging:
   -h           - print this message
   -H           - print detailed info on the scanners
   -V           - print version number
   -z nn        - start on page nn
   -dN          - debug mode (see source code
   -Z           - zap (erase) output directory

Control of Scanners:
   -P <dir>     - Specifies a plugin directory
   -E scanner   - turn off all scanners except scanner
   -m <max>     - maximum number of minutes to wait for memory starvation
                  default is 60
   -s name=value - sets a bulk extractor option name to be value

   -e bulk - enable scanner bulk
   -e wordlist - enable scanner wordlist

   -x accts - disable scanner accts
   -x aes - disable scanner aes
   -x base16 - disable scanner base16
   -x base64 - disable scanner base64
   -x elf - disable scanner elf
   -x email - disable scanner email
   -x exif - disable scanner exif
   -x gps - disable scanner gps
   -x gzip - disable scanner gzip
   -x hiber - disable scanner hiber
   -x json - disable scanner json
   -x kml - disable scanner kml
   -x net - disable scanner net
   -x pdf - disable scanner pdf
   -x vcard - disable scanner vcard
   -x windirs - disable scanner windirs
   -x winpe - disable scanner winpe
   -x winprefetch - disable scanner winprefetch
   -x zip - disable scanner zip
``

```

Example Usage
-------

Links
-------
[1] http://www.forensicswiki.org/wiki/Bulk_extractor
