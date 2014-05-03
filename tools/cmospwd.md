# cmospwd

Notes
-------
CmosPwd decrypts password stored in cmos used to access BIOS SETUP.
Works with the following BIOSes
 * ACER/IBM BIOS
 * AMI BIOS
 * AMI WinBIOS 2.5
 * Award 4.5x/4.6x/6.0
 * Compaq (1992)
 * Compaq (New version)
 * IBM (PS/2, Activa, Thinkpad)
 * Packard Bell
 * Phoenix 1.00.09.AC0 (1994), a486 1.03, 1.04, 1.10 A03, 4.05 rev 1.02.943, 4.06 rev 1.13.1107
 * Phoenix 4 release 6 (User)
 * Gateway Solo - Phoenix 4.0 release 6
 * Toshiba
 * Zenith AMI
With CmosPwd, you can also backup, restore and erase/kill cmos.[1]


Help Text
-------
```
CmosPwd - BIOS Cracker 5.0, October 2007, Copyright 1996-2007
GRENIER Christophe, grenier@cgsecurity.org
http://www.cgsecurity.org/

Usage: cmospwd [/k[de|fr]] [/d]
       cmospwd [/k[de|fr]] [/d] /[wlr] cmos_backup_file           write/load/restore
       cmospwd /k                                          kill cmos
       cmospwd [/k[de|fr]] /m[01]*	execute selected module

 /kfr french AZERTY keyboard, /kde german QWERTZ keyboard
 /d to dump cmos
 /m0010011 to execute module 3,6 and 7

NB: For Award BIOS, passwords are differents than original, but work.

```

Example Usage
-------

Links
-------
1. [cgsecurity](http://www.cgsecurity.org/wiki/CmosPwd)
