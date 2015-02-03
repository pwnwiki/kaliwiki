# fcrackzip

Notes
-------
Free/Fast Zip Password Cracker

fcrackzip searches each zipfile given for encrypted files and tries  to guess the password. All files must be encrypted with the same password, the more files you provide, the better.


Help Text
-------
```
USAGE: fcrackzip
          [-b|--brute-force]            use brute force algorithm
          [-D|--dictionary]             use a dictionary
          [-B|--benchmark]              execute a small benchmark
          [-c|--charset characterset]   use characters from charset
          [-h|--help]                   show this message
          [--version]                   show the version of this program
          [-V|--validate]               sanity-check the algortihm
          [-v|--verbose]                be more verbose
          [-p|--init-password string]   use string as initial password/file
          [-l|--length min-max]         check password with length min to max
          [-u|--use-unzip]              use unzip to weed out wrong passwords
          [-m|--method num]             use method number "num" (see below)
          [-2|--modulo r/m]             only calculcate 1/m of the password
          file...                    the zipfiles to crack

methods compiled in (* = default):

 0: cpmask
 1: zip1
*2: zip2, USE_MULT_TAB

```

Example Usage
-------
```
       fcrackzip -c a -p aaaaaa sample.zip
              checks  the  encrypted  files  in sample.zip for all lowercase 6
              character passwords (aaaaaa ... abaaba ... ghfgrg ... zzzzzz).

       fcrackzip --method cpmask --charset A --init AAAA test.ppm
              checks the obscured image test.ppm for all four character  pass
              words.

       fcrackzip -D -p passwords.txt sample.zip
              check for every password listed in the file passwords.txt.

```

Links
-------
1. [hyc/fcrackzip](https://github.com/hyc/fcrackzip)

