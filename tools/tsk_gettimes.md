# tsk_gettimes

Notes
-------
tsk_gettimes examines each of the file systems in a disk image and returns the data about them in the MAC‐time body format (the same as running 'fls -m' on each file system). The output of this can be used as input to mactime to make a timeline of file activity. The data is printed to STDOUT, which can then be redirected to a file.


Help Text
-------
```
usage: tsk_gettimes [-vV] [-i imgtype] [-b dev_sector_size] [-z zone] [-s seconds] image [image]
	-i imgtype: The format of the image file (use '-i list' for supported types)
	-b dev_sector_size: The size (in bytes) of the device sectors
	-v: verbose output to stderr
	-V: Print version
	-z: Time zone of original machine (i.e. EST5EDT or GMT) (only useful with -l)
	-s seconds: Time skew of original machine (in seconds) (only useful with -l & -m)


```

Example Usage
-------
To collect data about image image.dd:
```
 # tsk_gettimes ./image.dd > body.txt
```

Links
-------

