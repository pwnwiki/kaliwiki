# davtest

Notes
-------

Help Text
-------
```
/usr/bin/davtest -url <url> [options]

 -auth+ 	Authorization (user:password)
 -cleanup	delete everything uploaded when done
 -directory+	postfix portion of directory to create
 -debug+	DAV debug level 1-3 (2 & 3 log req/resp to /tmp/perldav_debug.txt)
 -move		PUT text files then MOVE to executable
 -nocreate 	don't create a directory
 -quiet	 	only print out summary
 -rand+ 	use this instead of a random string for filenames
 -sendbd+	send backdoors:
			auto - for any succeeded test
			ext - extension matching file name(s) in backdoors/ dir
 -uploadfile+	upload this file (requires -uploadloc)
 -uploadloc+	upload file to this location/name (requires -uploadfile)
 -url+		url of DAV location

Example: /usr/bin/davtest -url http://localhost/davdir

```

Example Usage
-------

Links
-------

