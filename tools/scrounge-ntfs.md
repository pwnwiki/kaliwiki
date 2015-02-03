# scrounge-ntfs

Notes
-------
scrounge-ntfs is a utility that can rescue data from corrupted NTFS partitions. It writes the files retrieved to another working file system. Certain information about the partition needs to be known in advance.

The -l mode is meant to be run in advance of the data corruption, with the output stored away in a file. This allows scrounge-ntfs to recover data reliably. See the 'NOTES' section below for recover info when this isn't the case.


Help Text
-------
```
usage: scrounge -l disk                                              
  List all drive partition information.                              
                                                                     
usage: scrounge -s disk                                              
  Search drive for NTFS partitions.                                  
                                                                     
usage: scrounge [-m mftoffset] [-c clustersize] [-o outdir] disk start end  
  Scrounge data from a partition                                     
  -m         Offset to mft (in sectors)                              
  -c         Cluster size (in sectors, default of 8)                 
  -o         Directory to put scrounged files in                     
  disk       The raw disk partitios (ie: /dev/hda)                   
  start      First sector of partition                               
  end        Last sector of partition              

```

Example Usage
-------

Links
-------

