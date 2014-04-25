# reglookup

Notes
-------
reglookup is designed to read windows registry elements and print them out to stdout in a CSV-like format. It has filtering options to narrow the focus of the output. 
This tool is designed to work with on Windows NT-based registries.


Help Text
-------
```
Usage: reglookup [-v] [-s] [-p <PATH_FILTER>] [-t <TYPE_FILTER>] <REGISTRY_FILE>
Version: 0.12.0
Options:
	-v	 sets verbose mode.
	-h	 enables header row. (default)
	-H	 disables header row.
	-s	 enables security descriptor output.
	-S	 disables security descriptor output. (default)
	-p	 restrict output to elements below this path.
	-t	 restrict results to this specific data type.
	-i	 includes parent key modification times with child values.

```

Example Usage
-------
To read and print the contents of an entire system registry file:
```
 reglookup /mnt/win/c/WINNT/system32/config/system
```

To limit the output to just those entries under the Services key:
``` 
 reglookup -p /ControlSet002/Services /mnt/win/c/WINNT/system32/config/system
```

To limit the output to all registry values of type BINARY:
```
 reglookup -t BINARY /mnt/win/c/WINNT/system32/config/system
```

And to limit the output to BINARY values under the Services key:
``` 
 reglookup -t BINARY -p /ControlSet002/Services /mnt/win/c/WINNT/system32/config/system
```

Links
-------
[1] http://projects.sentinelchicken.org/reglookup/
