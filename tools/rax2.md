# rax2

Notes
-------

The rax2 utility aims to be a minimalistic expression evaluator for the shell.

Help Text
-------
```
$ rax2 -h

Usage: rax2 [options] [expr ...]
int   ->  hex           ;  rax2 10
hex   ->  int           ;  rax2 0xa
-int  ->  hex           ;  rax2 -77
-hex  ->  int           ;  rax2 0xffffffb3
int   ->  bin           ;  rax2 b30
bin   ->  int           ;  rax2 1010d
float ->  hex           ;  rax2 3.33f
hex   ->  float         ;  rax2 Fx40551ed8
oct   ->  hex           ;  rax2 35o
hex   ->  oct           ;  rax2 Ox12 (O is a letter)
bin   ->  hex           ;  rax2 1100011b
hex   ->  bin           ;  rax2 Bx63
raw   ->  hex           ;  rax2 -S < /binfile
hex   ->  raw           ;  rax2 -s 414141
-b    binstr -> bin     ;  rax2 -b 01000101 01110110
-B    keep base         ;  rax2 -B 33+3 -> 36
-d    force integer     ;  rax2 -d 3 -> 3 instead of 0x3
-e    swap endianness   ;  rax2 -e 0x33
-f    floating point    ;  rax2 -f 6.3+2.1
-h    help              ;  rax2 -h
-k    randomart         ;  rax2 -k 0x34 1020304050
-n    binary number     ;  rax2 -e 0x1234   # 34120000
-s    hexstr -> raw     ;  rax2 -s 43 4a 50
-S    raw -> hexstr     ;  rax2 -S < /bin/ls > ls.hex
-t    tstamp -> str     ;  rax2 -t 1234567890
-x    hash string       ;  rax2 -x linux osx
-u    units             ;  rax2 -u 389289238 # 317.0M
-v    version           ;  rax2 -V
```

Example Usage
-------


```

```

Links
-------
[Radare2book](http://maijin.github.io/radare2book/introduction/rax2.html)
