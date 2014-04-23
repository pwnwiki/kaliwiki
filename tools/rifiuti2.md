# rifiuti2

Notes
-------
Rifiuti2 is a rewrite of rifiuti, a great tool from Foundstone folks for analyzing Windows Recycle Bin INFO2 file. Analysis of Windows Recycle Bin is usually carried out during Windows computer forensics. Rifiuti2 can extract file deletion time, original path and size of deleted files and whether the deleted files have been moved out from the recycle bin since they are trashed. Rifiuti2 supports the INFO2 file format found in Windows up to Windows XP and the new file format found in Vista, and the program is fully internationalized. If you need to analyse recycle bins of Windows Vista and Windows Server 2008, you should use the rifiuti-vista command, for other Windows platforms, you should use the rifiuti command.

Quoting from original Foundstone page:
```
Many computer crime investigations require the reconstruction of a subject's Recycle Bin. Since this analysis technique is executed regularly, we researched the structure of the data found in the Recycle Bin repository files (INFO2 files). Rifiuti, the Italian word meaning "trash", was developed to examine the contents of the INFO2 file in the Recycle Bin. ... Rifiuti is built to work on multiple platforms and will execute on Windows (through Cygwin), Mac OS X, Linux, and *BSD platforms."
```
Since the original rifiuti (last updated 2004) is restricted to English version of Windows (fail to analyze any non-latin character), thus this rewrite. But it does more:

	* Supports Windows in any other languages besides English
    * Supports Vista and 2008 (they don't use INFO2 file any more)
    * Enables localization (that is, translatable)
    * More rigorous error checking
    * Supports output in XML format



Help Text
-------
```
Usage:
  rifiuti2 [OPTION...] FILE

Help Options:
  -h, --help                 Show help options
  --help-all                 Show all help options
  --help-text                Show plain text output options

Application Options:
  -o, --output=FILE          Write output to FILE
  -x, --xml                  Output in XML format (-t, -n, -l, -8 options will have no effect)
  --from-encoding=ENC        The assumed file name character set when no unicode file name is present in INFO2 record (mandatory if INFO2 file is created by Win98, useless otherwise)


```

Example Usage
-------

Links
-------

