# UATester

Notes
-------

Help Text
-------
```

         _/    _/  _/_/_/_/       _/_/_/_/ _/_/_/_/ _/_/_/_/ _/_/_/_/ _/_/_/_/ _/_/_/_/
        _/    _/  _/    _/          _/    _/       _/          _/    _/       _/    _/
       _/    _/  _/_/_/_/  _/_/_/  _/    _/_/_/   _/_/_/_/    _/    _/_/_/   _/_/_/_
      _/    _/  _/    _/          _/    _/             _/    _/    _/       _/    _/
     _/_/_/_/  _/    _/          _/    _/_/_/_/ _/_/_/_/    _/    _/_/_/_/ _/      _/ [v1.06]

                                                                 _/ User-Agent Tester ?
                                                                  _/ AKA: Purple Pimp ?
                                                                    _/ ChrisJohnRiley ?
                                                                       _/ blog.c22.cc ?



  This tool is designed to automatically check a given URL using a list of standard and non-
  standard User Agent strings provided by the user (1 per line).
  
  The results of these checks are then reported to the user for further manual analysis where 
  required. Gathered data includes Response Codes, resulting URL in the case of a 30x response,
  MD5 and length of response body, and select Server headers.

  Results: When in non-verbose mode, only values that do not match the initial reference connection
  are reported to the user. If no results are shown for a specific useragent then all results match
  the initial reference connection. If you require a full output of all checks regardless of matches
  to the reference, please use the verbose setting.
  
     Output:  [+] Added Headers, [-] Removed Headers, [!] Altered Headers, [ ] No Change 

  Usage .:
            -u / --url Complete URL
            -f / --file <Path to User Agent file> / If no file is provided, -d options must be present
            -s / --single provide single user-agent string (may need to be contained within quotes)
            -d / --default Select the UA String type(s) to check. Select 1 or more of the following ?
            	           catagories. (M)obile, (D)esktop, mis(C), (T)ools, (B)ots, e(X)treme [!])
			
	    -o / --output <Path to output file> CSV formated output (FILE WILL BE OVERWRITTEN[!])
	    -v / --verbose results (Displays full headers for each check) >> Recommended
            --debug See debug messages (This isn't the switch you're looking for)


  Example .:

	    ./UATester.py -u www.example.com -f ./useragentlist.txt -v
	    ./UATester.py -u https://www.wordpress.com
	    ./UATester.py -u http://www.defaultserver.com -v --debug
	    ./UATester.py -u facebook.com -v -d MDBX
	    ./UATester.py -u https://www.google.com -s "MySpecialUserAgent"
	    ./UATester.py -u blog.c22.cc -d MC -o ./output.csv

```

Example Usage
-------

Links
-------

