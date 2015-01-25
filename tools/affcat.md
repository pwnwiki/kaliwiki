# affcat

Notes
-------
affcat outputs the contents of an image file to stdout. Image files that are not raw but are recognized by AFF will be output in raw format. Missing pages will not be padded, but the fact that they are missing will be noted on STDERR.

Part of Afflib



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
Note: there is some confustion about the file name. If you look at the help text it is referred to as afcat. However in both the github library and kali, the file name is affcat.

Below stolen from: [opensourceforu](http://www.opensourceforu.com/2011/03/digital-forensic-analysis-using-backtrack-part-1/)

Afcat is a command-line utility that prints the various contents of an AFF image file. Basic usage is `afcat <options> <AFF file name>`. Some of the useful options are:
```
-p <nnn> — Output data of page number <nnn>.
-S <nnn> — Output data of sector <nnn> (sector size 512 bytes).
-l — Output all segment names.
-L — Output all segment names, arg and segment length.
```
Example: Invoking Afcat on the AFF file `/tmp/image.aff` with the `-L` option prints an output as shown below

![output of affinfo](http://www.opensourceforu.com/wp-content/uploads/2011/03/fig7-afcat.jpg)

Links
-------
1. [afflib github page](https://github.com/simsong/AFFLIBv3)
1. [opensourceforu](http://www.opensourceforu.com/2011/03/digital-forensic-analysis-using-backtrack-part-1/)
