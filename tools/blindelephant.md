# blindelephant

Notes
-------
The BlindElephant Web Application Fingerprinter attempts to discover the version of a web application by comparing static files at known locations against precomputed hashes for versions of those files in all available releases. The technique is fast, low-bandwidth, non-invasive, generic, and highly automatable.

Help Text
-------
```
Usage: BlindElephant.py [options] url appName

Options:
  -h, --help            show this help message and exit
  -p PLUGINNAME, --pluginName=PLUGINNAME
                        Fingerprint version of plugin (should apply to web app
                        given in appname)
  -s, --skip            Skip fingerprinting webpp, just fingerprint plugin
  -n NUMPROBES, --numProbes=NUMPROBES
                        Number of files to fetch (more may increase accuracy).
                        Default: 15
  -w, --winnow          If more than one version are returned, use winnowing
                        to attempt to narrow it down (up to numProbes
                        additional requests).
  -l, --list            List supported webapps and plugins
  -u, --updateDB        Pull latest DB files from
                        blindelephant.sourceforge.net repo (Equivalent to svn
                        update on blindelephant/dbs/). May require root if
                        blindelephant was installed with root.

Use "guess" as app or plugin name to attempt to attempt to
discover which supported apps/plugins are installed.
```

Example Usage
-------

Links
-------
[Blindelephant Sourseforge project](http://blindelephant.sourceforge.net/)
