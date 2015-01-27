# ragg2

Notes
-------
radare2 utility to run programs in exotic environments. ragg2-cc is a frontend of CC. 
It is used to creates tiny binaries (1KB) or shellcodes in binary or hexpairs from a C source.


Help Text
-------
```
ragg2 [options] [file|-]
 -a [x86|arm]    select architecture
 -b [32|64]      register size
 -k [os]         operating system's kernel (linux,bsd,osx,w32)
 -f [format]     output format (raw, pe, elf, mach0)
 -F              output native format (osx=mach0, linux=elf, ..)
 -o [file]       output file
 -O              use default output file (filename without extension or a.out)
 -I [path]       add include path
 -L              list all plugins (shellcodes and encoders)
 -i [shellcode]  include shellcode plugin, uses options. see -L
 -e [encoder]    use specific encoder. see -L
 -B [hexpairs]   append some hexpair bytes
 -c [k=v]        set configuration options
 -C [file]       append contents of file
 -d [off:dword]  patch dword (4 bytes) at given offset
 -D [off:qword]  patch qword (8 bytes) at given offset
 -w [off:hex]    patch hexpairs at given offset
 -p [padding]    add padding after compilation (padding=n10s32)
                 ntas : begin nop, trap, 'a', sequence
                 NTAS : same as above, but at beginning
 -s              show assembler
 -r              show raw bytes instead of hexpairs
 -x              execute
 -v              show version
 -h              show this help


```

Example Usage
-------


```

```

Links
-------
[Ubuntu Trusty ragg2 manpage](http://manpages.ubuntu.com/manpages/trusty/en/man1/ragg2.1.html)
