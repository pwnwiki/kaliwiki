# pev	

Notes
-------
Make an analysis and show useful information of PE32/PE32+ file given.

Help Text
-------
```
Usage: pev [-cdhops] <file>

pev will get information about PE32 binaries and display it on standard output.
All switches are optional, but --all is used by default.

```

Example Usage
-------
To get only the Product Version of putty.exe file:
```
 $ pev -p putty.exe
```

To show DOS and COFF file headers of cards.dll:
```
 $ pev -dc cards.dll
```

Display all possible information about svchost.exe file:
```
 $ pev svchost.exe
```

Links
-------

