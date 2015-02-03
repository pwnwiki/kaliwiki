# affcat

Notes
-------
affcat outputs the contents of an image file to stdout. Image files that are not raw but are recognized by AFF will be output in raw format. Missing pages will not be padded, but the fact that they are missing will be noted on STDERR.


Help Text
-------
```
afcat version 3.7.1
usage: afcat [options] infile [... more infiles]
options:
    -s name --- Just output segment name
    -p ###  --- just output data page number ###
    -S ###  --- Just output data sector ### (assumes 512-byte sectors). Sector #0 is first
    -q      --- quiet; don't print to STDERR if a page is skipped
    -n      --- noisy; tell when pages are skipped.
    -l      --- List all of the segment names
    -L      --- List segment names, lengths, and args
    -d      --- debug. Print the page numbers to stderr as data goes to stdout
    -b      --- Output BADFALG for bad blocks (default is NULLs)
    -v      --- Just print the version number and exit.
    -r offset:count --- seek to offset and output count characters in each file; may be repeated


```

Example Usage
-------

Links
-------

