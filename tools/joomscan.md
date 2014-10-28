# joomscan

Notes
-------
OWASP Joomla Vulnerability Scanner Project

Help Text
-------
```

 ..|''||   '|| '||'  '|'     |      .|'''.|  '||''|.  
.|'    ||   '|. '|.  .'     |||     ||..  '   ||   || 
||      ||   ||  ||  |     |  ||     ''|||.   ||...|' 
'|.     ||    ||| |||     .''''|.  .     '||  ||      
 ''|...|'      |   |     .|.  .||. |'....|'  .||.     
    

=================================================================
 OWASP Joomla! Vulnerability Scanner v0.0.4  
 (c) Aung Khant, aungkhant]at[yehg.net
 YGN Ethical Hacker Group, Myanmar, http://yehg.net/lab
 Update by: Web-Center, http://web-center.si (2011)
=================================================================
 
 Vulnerability Entries: 611
 Last update: February 2, 2012

 Usage:  ./joomscan.pl -u <string> -x proxy:port
         -u <string>      = joomla Url

         ==Optional==

         -x <string:int>  = proXy to tunnel
         -c <string>      = Cookie (name=value;)
         -g "<string>"    = desired useraGent string(within ") 
         -nv              = No Version fingerprinting check
         -nf              = No Firewall detection check
         -nvf/-nfv        = No version+firewall check
         -pe 		  = Poke version only and Exit
         -ot              = Output to Text file (target-joexploit.txt)
         -oh              = Output to Html file (target-joexploit.htm)
         -vu              = Verbose (output every Url scan)
	 -sp		  = Show completed Percentage

 ~Press ENTER key to continue 


 Example:  ./joomscan.pl -u victim.com -x localhost:8080
	  
 Check:    ./joomscan.pl check
           - Check if the scanner update is available or not.

 Update:   ./joomscan.pl update
           - Check and update the local database if newer version is available.

 Download: ./joomscan.pl download
           - Download the scanner latest version as a single zip file - joomscan-latest.zip.

 Defense:  ./joomscan.pl defense
           - Give a defensive note.

 About:    ./joomscan.pl story
           - A short story about joomscan.
 
 Read:     ./joomscan.pl read DOCFILE
           DOCFILE - changelog,release_note,readme,credits,faq,owasp_project

```

Example Usage
-------

Links
-------
[Joomscan Sourceforge project](http://sourceforge.net/projects/joomscan/)

[OWASP Joomscan project](https://www.owasp.org/index.php/Category:OWASP_Joomla_Vulnerability_Scanner_Project)

