# Radare2

Notes
-------
An open-source complete framework for reverse-engineering and analyzing binaries; composed of a set of small utilities that can be used together or independently from the command line.


Help Text
-------
```
Usage: radare2 [-dDwntLqv] [-P patch] [-p prj] [-a arch] [-b bits] [-i file]
               [-s addr] [-B blocksize] [-c cmd] [-e k=v] [file]
 -a [arch]    set asm.arch eval var
 -b [bits]    set asm.bits eval var
 -B [size]    initial block size
 -c 'cmd..'   execute radare command
 -d           use 'file' as a program to debug
 -D [backend] enable debug mode (e cfg.debug=true)
 -e k=v       evaluate config var
 -f           block size = file size
 -i [file]    run script file
 -l [lib]     load plugin file
 -L           list supported IO plugins
 -n           do not run ~/.radare2rc
 -q           quite mode (no prompt)
 -p [prj]     set project file
 -P [file]    apply rapatch file and quit
 -s [addr]    initial seek
 -t           load rabin2 info in thread
 -v           show radare2 version
 -w           open file in write mode
 -h           show this help
 -H           show extended help (files and environment)

```

Example Usage
-------


```

```

Links
-------
[Official site](http://www.radare.org/)

[Radare2 GitHub project](https://github.com/radare/radare2)

[radare2 book](http://maijin.github.io/radare2book/)

[The Official Radare Blog](http://radare.today/)

[Defeating ioli with radare2](http://dustri.org/b/defeating-ioli-with-radare2.html)

[Ubuntu Trusty radare2 manpage](http://manpages.ubuntu.com/manpages/trusty/en/man1/radare2.1.html)

[Reverse Engineering Embedded Software Using Radare2](https://github.com/pastcompute/lca2015-radare2-tutorial)
