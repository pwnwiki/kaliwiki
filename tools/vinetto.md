# vinetto

Notes
-------
Vinetto is a tool intended for forensics examinations. It is a console program to extract thumbnail images and their metadata from those thumbs.db files generated under Windows. Used in forensic environments.

Help Text
-------
```
Usage: vinetto [OPTIONS] [-o DIR] file

Options:
  --version   show program's version number and exit
  -h, --help  show this help message and exit
  -o DIR      write thumbnails to DIR
  -H          write html report to DIR

```

Example Usage
-------
How to display metadata contained within a Thumbs.db file
```
    $ vinetto /path/to/Thumbs.db
```
How to extract the related thumbnails to a directory
```
    $ vinetto -o /tmp/vinetto_output /path/to/Thumbs.db
```
How to extract the related thumbnails to a directory and produce an html report to preview these thumbnails through your favorite browser.
```
    $ vinetto -Ho /tmp/vinetto_output /path/to/Thumbs.db
```
How to get a metadata report on all non deleted Thumbs.db files contained within a partition
```
    $ find /mnt/hda2 -iname thumbs.db -printf "\n==\n %p \n\n" -exec vinetto {} \; 2>/tmp/vinetto_err.log >/tmp/vinetto_hda2.txt
```

Links
-------
[1] http://vinetto.sourceforge.net/
