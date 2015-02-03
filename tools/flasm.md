# Flasm

Notes
-------
Flasm is a free command line assembler/disassembler of Flash ActionScript bytecode. 
It lets you make changes to any SWF. Flasm fully supports SWFs produced by Macromedia Flash 8 and earlier Flash versions.

Help Text
-------
```
Flasm 1.62 build Feb 12 2011

(c) 2001 Opaque Industries, (c) 2002-2007 Igor Kogan, (c) 2005 Wang Zhen
All rights reserved. See LICENSE.TXT for terms of use.

Usage: flasm [command] filename

Commands:
   -d     Disassemble SWF file to the console
   -a     Assemble Flasm project (FLM)
   -u     Update SWF file, replace Flasm macros
   -b     Assemble actions to __bytecode__ instruction or byte sequence
   -z     Compress SWF with zLib
   -x     Decompress SWF

Backups with $wf extension are created for altered SWF files.

To save disassembly or __bytecode__ to file, redirect it:
flasm -d foo.swf > foo.flm
flasm -b foo.txt > foo.as


```

Example Usage
-------


```
flasm -d flash.swf
```

Links
-------
[Official site](http://www.nowrap.de/flasm)
