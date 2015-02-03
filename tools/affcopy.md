# affcopy

Notes
-------
affcopy - segment-by-segment copying and verification (optional encryption)

Help Text
-------
```
usage: afcopy [options] file1 file
                    Copies file1 to file2
       afcopy [options] file1 file2 file3 ... dir
                    Copies file1.. into dir
       afcopy [options] file1 file2 file3 ... dir1 dir2...
                    Copies file1.. into dirs1, dir2, ...

By default, all page MACs are verified on read and all segments
are verified after write.
Options:
   -v = verbose: print each file as it is copied
   -vv = very verbose: print each segment as it is copied
   -d = print debugging information as well
   -x = don't verify hashes on reads
   -y = don't verify writes
   -Xn = recompress pages (preen) with zlib level n
   -L  = recompress pages (preen) with LZMA (smaller but slower)

   -h = help; print this message.
   -V = print the program version and exit.
   -z = zap; copy even if the destination exists.
   -m = just copy the missing segments

Signature Options:
   -k filename.key   = specify private key for signing
   -c filename.cer   = specify a X.509 certificate that matches the private key
                       (by default, the file is assumed to be the same one
                       provided with the -k option.)   -n  = read notes to accompany the copy from standard in.


Encryption Options:   Specify passphrase encryption for filename.aff with:
      file://:passphrase@/filename.aff

Examples:
       afcopy  file.aff   file://:mypassword@/file-encrypted.aff   - encrypt file.aff
       afcopy -vy -X9 *.aff s3:///     Copy all files in current
                               directory to S3 default bucket with X9 compression

```

Example Usage
-------

Links
-------

