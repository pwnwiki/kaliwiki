# missidentify

Notes
-------
Miss Identify is a program to find Win32 applications. In its default mode it displays the filename of any executable that does not have an executable extension (i.e. exe, dll, com, sys, cpl, hxs, hxi, olb, rll, or tlb). The program can also be run to display all executables encountered, regardless of the extension. This is handy when looking for all of the executables on a drive. Other options allow the user to record the strings found in an executable and to work recursively.[1]

Help Text
-------
```
missidentify version 1.0 by Jesse Kornblum
Usage: missidentify [-Vh] [-rablv] [-s|-S len] [FILES]

-r  Recursive mode. All subdirectories are traversed
-q  Silent mode. No error messages are displayed
-a  Display all executable files regardless of extension
-b  Bare filename. No path information displayed
-l  Relative paths in filenames
-v  Verbose mode. Displays the filename for every 10th file processed
-s|-S Display strings
-V  Display version number and exit
-h  Display this help message

```

Example Usage
-------
Taken from forensicswiki[1]

The program can be used to search for mislabeled executables:
```
C:\> missidentify *
C:\missidentify-1.0\sample.jpg
```

To enumerate all executables:
```
C:\> missidentify -a * 
C:\missidentify-1.0\sample.jpg
C:\missidentify-1.0\missidentify.exe
```

To search for all executables in an unusual place:
```
C:\> missidentify -ar c:\windows\system32
...
C:\WINDOWS\System32\ntdll.dll
C:\WINDOWS\System32\ntoskrnl.exe
C:\WINDOWS\System32\NEVER-GONNA-CATCH-ME.EXE
C:\WINDOWS\System32\ntver.dll
...
```

Links
-------
[1] http://www.forensicswiki.org/wiki/Miss_Identify
