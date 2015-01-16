# rahash2

Notes
-------
This program is part of the radare project.

Hasher allows you to calculate, check and show the hash values of each block of a target file. The block size is 32768 bytes by default. It's allowed to hash from stdin using '-' as a target file.
You can hash big files by hashing each block and later determine what part of it has been modified. Useful for filesystem analysis. Algorithms that are supported : md4, md5, crc16, crc32, sha1, sha256, sha384, sha512, par, xor, xorpair, mod255, hamdist, entropy, all.
This command can be used to calculate hashes of a certain part of a file or a command line passed string.


Help Text
-------
```
Usage: rahash2 [-rBv] [-b bsize] [-a algo] [-s str] [-f from] [-t to] [file] ...
 -a algo     comma separated list of algorithms (default is 'sha1')
 -b bsize    specify the size of the block (instead of full file)
 -B          show per-block hash
 -s string   hash this string instead of files
 -f from     start hashing at given address
 -t to       stop hashing at given address
 -r          output radare commands
 -v          show version information
Supported algorithms: md4, md5, sha1, sha256, sha384, sha512, crc16,
    crc32, xor, xorpair, parity, mod255, hamdist, entropy, pcprint


```

Example Usage
-------

Links
-------
[Radare2book](http://maijin.github.io/radare2book/rahash2/intro.html)
