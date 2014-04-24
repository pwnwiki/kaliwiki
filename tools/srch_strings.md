# srch_strings

Notes
-------
Display printable strings in [file(s)] (stdin by default)

Help Text
-------
```
Usage: srch_strings [option(s)] [file(s)]
 Display printable strings in [file(s)] (stdin by default)
 The options are:
  -a -                 Scan the entire file, not just the data section
  -f       Print the name of the file before each string
  -n number       Locate & print any NUL-terminated sequence of at
  -<number>                 least [number] characters (default 4).
  -t {o,x,d}        Print the location of the string in base 8, 10 or 16
  -o                        An alias for --radix=o
  -e {s,S,b,l,B,L} Select character size and endianness:
                            s = 7-bit, S = 8-bit, {b,l} = 16-bit, {B,L} = 32-bit
  -h                  Display this information
  -v               Print the program's version number

```

Example Usage
-------
```
root@kali:~/kaliwiki/tools# srch_strings -a /root/samples/nbtscan.exe
<...>
osize > 1
obuf != 0
nbtscan 1.0.35 - 2008-04-08 - http://www.unixwiz.net/tools/
targ != 0
targets.c
paddr != 0
currTarget != 0
    'NBTSCAN' => {
    ],
	%s,
    'CMDLINE' => [
    'DATE'    => %s,
# use as  'my $ref = do filename;'
# perl hashref output
argv != 0
gen_perl.c
\x%02X
<...>
```

Links
-------
