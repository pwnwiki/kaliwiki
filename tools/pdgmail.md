# pdgmail

Notes
-------
Gather gmail artifacts from a pd process memory dump

Help Text
-------
```
Usage: /usr/bin/pdgmail [OPTIONS]

Options:
   -f, --file       the file to use (stdin if no file given)
   -b, --bodies	    don't look for message bodies (helpful if you're getting too many false positives on the mb regex)
   -h, --help	    prints this 
   -v,--verbose	    be verbose (prints filename, other junk)
   -V,--version     prints just the version info and exits.
   
This expects to be unleashed on the result of running strings -el on a pd dump from windows process memory. 
Anything other than that, your mileage will certainly vary.

```

Example Usage
-------
```
strings -el memory.dump | pdgmail | less
```

Links
-------
[1] http://digital-forensics.sans.org/blog/2008/10/20/pdgmail-new-tool-for-gmail-memory-forensics/
