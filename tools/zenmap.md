# zenmap

Notes
-------
Zenmap is the official Nmap Security Scanner GUI. It is a multi-platform (Linux, Windows, Mac OS X, BSD, etc.) free and open source application which aims to make Nmap easy for beginners to use while providing advanced features for experienced Nmap users. Frequently used scans can be saved as profiles to make them easy to run repeatedly. A command creator allows interactive creation of Nmap command lines. Scan results can be saved and viewed later. Saved scan results can be compared with one another to see how they differ. The results of recent scans are stored in a searchable database. 

Help Text
-------
```
Usage: zenmap [options] [result files]

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  --confdir=DIR         Use DIR as the user configuration directory. Default:
                        /root/.zenmap
  -f RESULT_FILES, --file=RESULT_FILES
                        Specify a scan result file in Nmap XML output format.
                        Can be used more than once to specify several scan
                        result files.
  -n, --nmap            Run Nmap with the specified args.
  -p PROFILE, --profile=PROFILE
                        Begin with the specified profile selected. If combined
                        with the -t (--target) option, automatically run the
                        profile against the specified target.
  -t TARGET, --target=TARGET
                        Specify a target to be used along with other options.
                        If specified alone, open with the target field filled
                        with the specified target
  -v, --verbose         Increase verbosity of the output. May be used more
                        than once to get even more verbosity
```

Example Usage
-------

Links
-------
