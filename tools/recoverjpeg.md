# recoverjpeg

Notes
-------
Recoverjpeg tries to identify jpeg pictures from a filesystem image. To achieve this goal, it scans the filesystem image and looks for a jpeg structure at blocks starting at 512 bytes boundaries.

Salvaged jpeg pictures are stored by default under the name imageXXXXX.jpg where XXXXX is a five digit number starting at zero. If there are more than 100,000 recovered pictures, recoverjpeg will
start using six figures numbers and more as soon as needed, but the 100,000 first ones will use a five figures number. Options -f and -i can override this behaviour.


Help Text
-------
```
Usage: recoverjpeg [options] file|device
Options:
   -b blocksize   Block size in bytes (default: 512)
   -f format      Format string in printf syntax
   -h             This help message
   -i index       Initial picture index
   -m maxsize     Max jpeg file size in bytes (default: 6m)
   -q             Be quiet
   -r readsize    Size of disk reads in bytes (default: 128m)
   -v verbose     Replace progress bar by details


```

Example Usage
-------
Recover as many pictures as possible from the memory card located in /dev/sdc:
```
 recoverjpeg /dev/sdc
```

Recover as many pictures as possible from a crashed ReiserFS file system (which does not necessarily store pictures at block boundaries) in /dev/hdb1:
```
 recoverjpeg -b 1 /dev/hdb1
```

Do the same thing in a memory constrained environment where no more than 16MB of RAM can be used for the operation:
```
 recoverjpeg -b 1 -r 16m /dev/hdb1
```

Links
-------

