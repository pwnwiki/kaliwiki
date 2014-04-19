# wfuzz

Notes
-------

Help Text
-------
```
********************************************************
* Wfuzz  2.0 - The Web Bruteforcer                     *
********************************************************

Usage: /usr/bin/wfuzz [options] <url>

Options:
-c			    : Output with colors
-v			    : Verbose information
-o printer		    : Output format by stderr

-p addr			    : use Proxy (ip:port or ip:port-ip:port-ip:port)
-x type			    : use SOCK proxy (SOCKS4,SOCKS5)
-t N			    : Specify the number of threads (20 default)
-s N			    : Specify time delay between requests (0 default)

-e <type>		    : List of available encodings/payloads/iterators/printers
-R depth		    : Recursive path discovery
-I			    : Use HTTP HEAD instead of GET method (No HTML body responses). 
--follow		    : Follow redirections

-m iterator		    : Specify iterator (product by default)
-z payload		    : Specify payload (type,parameters,encoding)
-V alltype		    : All parameters bruteforcing (allvars and allpost). No need for FUZZ keyword.

-X			    : Payload within HTTP methods (ex: "FUZZ HTTP/1.0"). No need for FUZZ keyword.
-b cookie		    : Specify a cookie for the requests
-d postdata 		    : Use post data (ex: "id=FUZZ&catalogue=1")
-H headers  		    : Use headers (ex:"Host:www.mysite.com,Cookie:id=1312321&user=FUZZ")

--basic/ntlm/digest auth    : in format "user:pass" or "FUZZ:FUZZ" or "domain\FUZ2Z:FUZZ"

--hc/hl/hw/hh N[,N]+	    : Hide resposnes with the specified[s] code/lines/words/chars (Use BBB for taking values from baseline)
--hs regex		    : Hide responses with the specified regex within the response

Keyword: FUZZ,FUZ2Z  wherever you put these words wfuzz will replace them by the payload selected. 

Example: - wfuzz.py -c -z file,commons.txt --hc 404 -o html http://www.site.com/FUZZ 2> res.html
	 - wfuzz.py -c -z file,users.txt -z file,pass.txt --hc 404 http://www.site.com/log.asp?user=FUZZ&pass=FUZ2Z
	 - wfuzz.py -c -z range,1-10 --hc=BBB http://www.site.com/FUZZ{something}

	   More examples in the README.

```

Example Usage
-------

Links
-------

