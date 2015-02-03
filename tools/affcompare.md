# affcompare 

Notes
-------
affcompare - compares two disk images

Help Text
-------
```
affcompare version 3.7.1

usage: affcompare [options] file1 file2
       compares file1 with file2

or     affcompare [options] -r dir1 dir2
       comparses similarly-named files in dir1 and dir2

or     affcompare [options] -s file1 file2...
       Reports if file was successfully copied to Amazon S3
       checking only for existence, not reading back the bytes.
       (Because all writes to S3 are validated by the MD5 of the object
fast options:
(These compare segments but not their contents.)
       -p        --- report about the results of preening
       -e        --- Just report about existence (use with -r)
       -s        --- Just see if all of the segments are present, but don't
                     validate the contents. (Primarily for use with Amazon S3)
other options:
       -V        --- just print the version number and exit
       -v        --- Verbose; each file as it is compared.
       -q        --- Quiet. No output except for errors
       -a        --- print what's the same (all)
       -b        --- print the numbers of differing sectors
       -c        --- print the contents of differing sectors
       -m        --- Just report about the data (ignore metadata)
       -P ###    --- Just examine the differences on page ###
       -q        --- Quiet; no output except for errors.

Options documented above:
       -r dir1 dir2 --- recursively compare what's in dir1 with dir2, and
                       report what's in dir1 that's not in dir2
       -s        --- Check to see if named files are on Amazon S3

  affcompare file1.aff file2.aff           --- compare file1.aff and file2.aff
  affcompare f1.aff f2.aff dir1/           --- compare f1.aff with dir1/f1.aff and f2.aff with dir2/f2.aff
                                              note: dir1/ must end with a slash.
  affcompare -b img file.aff               --- compare file.aff and file.img
  affcompare -b img file1.aff file2.aff... --- compare file1.aff, file1.img, etc.
  affcompare -re dir1 dir2                --- report AFF files in dir1 but not in dir2
  affcompare -rse dir1 s3:///             --- report AFF files in dir1 but not on S3 (low bandwidth)
  affcompare -rs dir1 s3:///              --- report AFF files in dir1 but incomplete on on S3 (more bandwidth)

```

Example Usage
-------

Links
-------

