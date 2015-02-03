# affsign

Notes
-------

Help Text
-------
```
afsign version 3.7.1
usage: afsign [options] filename.aff
This program will:
  * Sign each segment if there are no segment signatures.
  * Write signed chain-of-custody Bill of Materials segment.

Signature Options:
   -k filename.key   = specify private key for signing
   -c filename.cer   = specify a X.509 certificate that matches the private key
                       (by default, the file is assumed to be the same one
                       provided with the -k option.)
   -Z                = ZAP (remove) all signature segments.
options:
    -n      --- ask for a chain-of-custody note.
    -v      --- Just print the version number and exit.

```

Example Usage
-------

Links
-------

