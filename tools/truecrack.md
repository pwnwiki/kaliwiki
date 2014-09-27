# Truecrack

Notes
-------
Truecrack performs bruteforce password attacks on Truecrypt containers. It works on Linux and it is optimized for Nvidia Cuda technology.

Help Text
-------
```
TrueCrack v3.0
Website: http://code.google.com/p/truecrack
Contact us: infotruecrack@gmail.com
Bruteforce password cracker for Truecrypt volume. Optimazed with Nvidia Cuda technology.
Based on TrueCrypt, freely available at http://www.truecrypt.org/
Copyright (c) 2011 by Luca Vaccaro.

Usage:
 truecrack -t <truecrypt_file> -k <ripemd160|sha512|whirlpool> -w <wordlist_file> [-b <parallel_block>]
 truecrack -t <truecrypt_file> -k <ripemd160|sha512|whirlpool> -c <charset> [-s <minlength>] -m <maxlength> [-b <parallel_block>]

Options:
 -h --help            			Display this information.
 -t --truecrypt <truecrypt_file>  	Truecrypt volume file.
 -k --key <ripemd160 | sha512 | whirlpool>  	Key derivation function (default ripemd160).
 -b --blocksize <parallel_blocks>   	Number of parallel computations (board dependent).
 -w --wordlist <wordlist_file>  	File of words, for Dictionary attack.
 -c --charset <alphabet>		Alphabet generator, for Alphabet attack.
 -s --startlength <minlength>		Starting length of passwords, for Alphabet attack (default 1).
 -m --maxlength <maxlength>		Maximum length of passwords, for Alphabet attack.
 -r --restore <number>			Restore the computation.
 -v --verbose         			Show computation messages.

Sample:
 Dictionary mode: truecrack --truecrypt ./volume --wordlist ./dictionary.txt 
 Charset mode: truecrack --truecrypt ./volume --charset ./dictionary.txt --maxlength 10

```

Example Usage
-------

```
truecrack --truecrypt <container.tc> --wordlist <password.txt>

```
Links
-------
[Truecrack project hosting](https://code.google.com/p/truecrack/)
