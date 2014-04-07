# sfuzz - Simple Fuzzer

Notes
-------

Help Text
-------
```
		Simple Fuzzer
By:	 Aaron Conole
version: 0.7.0
url:	 http://aconole.brad-x.com/programs/sfuzz.html
EMAIL:	 apconole@yahoo.com
Build-prefix: /usr
	-h	 This message.
	-V	 Version information.

networking / output:
	-v	 Verbose output
	-q	 Silent output mode (generally for CLI fuzzing)
	-X	 prints the output in hex

	-b	 Begin fuzzing at the test specified.
	-e	 End testing on failure.
	-t	 Wait time for reading the socket
	-S	 Remote host
	-p	 Port
	-T|-U|-O TCP|UDP|Output mode
	-R	 Refrain from closing connections (ie: "leak" them)

	-f	 Config File
	-L	 Log file
	-n	 Create a new logfile after each fuzz
	-r	 Trim the tailing newline
	-D	 Define a symbol and value (X=y).
	-l	 Only perform literal fuzzing
	-s	 Only perform sequence fuzzing

```

Example Usage
-------

Links
-------

