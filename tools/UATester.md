# UATester

Notes
-------
User Agent String Tester

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
Note: this tool is called in kali with `/usr/bin/ua-tester` or just `root@kali:~# ua-tester` not with the named python script in all of the help files.

Note 2: when run against https://www.wordpress.com `ua-tester -u https://www.wordpress.com` this script crashes. I have no idea why, but I haven't spent a lot of time troubleshooting. If you know what's going on, please let us know! 

```
  Example .:

	    ./UATester.py -u www.example.com -f ./useragentlist.txt -v
	    ./UATester.py -u https://www.wordpress.com
	    ./UATester.py -u http://www.defaultserver.com -v --debug
	    ./UATester.py -u facebook.com -v -d MDBX
	    ./UATester.py -u https://www.google.com -s "MySpecialUserAgent"
	    ./UATester.py -u blog.c22.cc -d MC -o ./output.csv
```
Outputs 

Basic test of http://www.google.com

```
root@kali:/usr/bin# ./ua-tester -u http://www.google.com


         _/    _/  _/_/_/_/       _/_/_/_/ _/_/_/_/ _/_/_/_/ _/_/_/_/ _/_/_/_/ _/_/_/_/
        _/    _/  _/    _/          _/    _/       _/          _/    _/       _/    _/
       _/    _/  _/_/_/_/  _/_/_/  _/    _/_/_/   _/_/_/_/    _/    _/_/_/   _/_/_/_
      _/    _/  _/    _/          _/    _/             _/    _/    _/       _/    _/
     _/_/_/_/  _/    _/          _/    _/_/_/_/ _/_/_/_/    _/    _/_/_/_/ _/      _/ [v1.06]

                                                                 _/ User-Agent Tester ↵
                                                                  _/ AKA: Purple Pimp ↵
                                                                    _/ ChrisJohnRiley ↵
                                                                       _/ blog.c22.cc ↵

 [>] Performing initial request and confirming stability
 [>] Using User-Agent string Mozilla/5.0 

    [ ] URL (ENTERED): http://www.google.com
    [ ] Response Code: 200 OK
    [ ] Date: Sat, 24 Jan 2015 17:07:24 GMT
    [ ] Expires: -1
    [ ] Cache-Control: private, max-age=0
    [ ] Content-Type: text/html; charset=UTF-8
    [ ] Set-Cookie: PREF=ID=ee4f13c2c4ae945d:FF=0:TM=1422119244:LM=1422119244:S=nbzlfHSSv_9FFWOn; expires=Mon,
	            23-Jan-2017 17:07:24 GMT; path=/; domain=.google.com
    [ ] Set-Cookie: NID=67=fTt3esYFSeWykAesKMn-SZ7wiRsqjk1xBXuq2s4wvg9T0jMjtUrGId2D5IldI2h_F8bM07kvrE5OKOpgOCp
	            lFyPNgtB5NjJzqgJQqk9PfO7pPUUPODfT74LIZK1wPKG0; expires=Sun, 26-Jul-2015 17:07:24 GMT; path=/;
	            domain=.google.com; HttpOnly
    [ ] P3P: CP="This is not a P3P policy! See
	            http://www.google.com/support/accounts/bin/answer.py?hl=en&answer=151657 for more info."
    [ ] Server: gws
    [ ] X-XSS-Protection: 1; mode=block
    [ ] X-Frame-Options: SAMEORIGIN
    [ ] Alternate-Protocol: 80:quic,p=0.02
    [ ] Accept-Ranges: none
    [ ] Vary: Accept-Encoding
    [ ] Connection: close
    [ ] Data (MD5): f1985331b98172538d53cfe19237f44f 

 [1] Pass
 [2] Pass
 [3] Pass

 [>] URL appears stable. Beginning test

 [>] Using DEFAULT User-Agent Strings


 [>] Output: [+] Added Headers, [-] Removed Headers, [!] Altered Headers, [ ] No Change


 [>] User-Agent String : Mozilla/5.0 (iPhone; U; CPU like Mac OS X; en) AppleWebKit/420+ (KHTML, like Gecko)
                         Version/3.0 Mobile/1A543a Safari/419.3


    [!] Cache-Control: private


 [>] User-Agent String : Mozilla/5.0 (iPad; U; CPU iPhone OS 3_2 like Mac OS X; en-us) AppleWebKit/531.21.10
                         (KHTML, like Gecko) Version/4.0.4 Mobile/7B314 Safari/531.21.10


    [!] Data (MD5): 77e50943c359ae2650d27da8d426f135


 [>] User-Agent String : Mozilla/5.0 (Linux; U; Android 2.1-update1; en-at; HTC Hero Build/ERE27)
                         AppleWebKit/530.17 (KHTML, like Gecko) Version/4.0 Mobile Safari/530.17


    [!] Cache-Control: private


 [>] User-Agent String : jBrowser-WAP


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : Nokia7650/1.0 Symbian-QP/6.1 Nokia/2.1


    [!] Content-Type: text/vnd.wap.wml; charset=ISO-8859-1


 [>] User-Agent String : Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; Trident/5.0)


    [!] URL (FINAL): https://www.google.com/?gws_rd=ssl
    [!] Response Code: 302 Found
    [!] Alternate-Protocol: 443:quic,p=0.02


 [>] User-Agent String : Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64; Trident/4.0)


    [!] URL (FINAL): https://www.google.com/?gws_rd=ssl
    [!] Response Code: 302 Found
    [!] Alternate-Protocol: 443:quic,p=0.02


 [>] User-Agent String : Mozilla/5.0 (Windows; U; MSIE 7.0; Windows NT 6.0; en-US)


    [!] Data (MD5): 56972665c3b6975e6e054c069427a520


 [>] User-Agent String : Mozilla/5.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 2.0.50727)


    [!] URL (FINAL): https://www.google.com/?gws_rd=ssl
    [!] Response Code: 302 Found
    [!] Alternate-Protocol: 443:quic,p=0.02


 [>] User-Agent String : Mozilla/4.0 (compatible;MSIE 5.5; Windows 98)


    [!] Data (MD5): bcab2383b361371109ce50e6aa08b606


 [>] User-Agent String : Mozilla/5.0 (Windows; U; Windows NT 6.1; ru; rv:1.9.2.3) Gecko/20100401 Firefox/4.0
                         (.NET CLR 3.5.30729)


    [!] Data (MD5): 47e08e5f044dbc1dc2093a10f9238be4


 [>] User-Agent String : Mozilla/5.0 (Windows NT 6.1; rv:2.0.1) Gecko/20100922 Firefox/4.0.1


    [!] Data (MD5): 40b39bd0824dade445a1a4e0bea8d242


 [>] User-Agent String : Mozilla/5.0 (Windows; U; Windows NT 5.2; rv:1.9.2) Gecko/20100101 Firefox/3.6


    [!] Data (MD5): 7c982c54ccbf6e37c3be8de132c6cf42


 [>] User-Agent String : Mozilla/5.0 (X11; U; SunOS sun4v; en-US; rv:1.8.1.3) Gecko/20070321 Firefox/2.0.0.3


    [!] Data (MD5): b5388816ea4d4b08c3c06c813a9d27a4


 [>] User-Agent String : Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit/534.7 (KHTML, like
                         Gecko) Chrome/7.0.514.0 Safari/534.7


    [!] Data (MD5): 1bc48eee18ad098b664f4bbb9f880d1d


 [>] User-Agent String : Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US) AppleWebKit/525.13 (KHTML, like
                         Gecko) Chrome/0.2.149.27 Safari/525.13


    [!] Data (MD5): 060a33a5657fb8c1c7ceb6a04d030691


 [>] User-Agent String : Mozilla/5.0 (Windows; U; Windows NT 5.2; en-US) AppleWebKit/533.17.8 (KHTML, like
                         Gecko) Version/5.0.1 Safari/533.17.8


    [!] Data (MD5): d245066d9832f4d58268439a19806f67


 [>] User-Agent String : Opera/9.99 (Windows NT 5.1; U; pl) Presto/9.9.9


    [!] Data (MD5): e3db6c4c45379076322b3613b4b97c62


 [>] User-Agent String : Windows-Media-Player/9.00.00.4503


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : Mozilla/5.0 (PLAYSTATION 3; 2.00)


    [!] Data (MD5): e5eab408a0f745d692cd738d92110e75


 [>] User-Agent String : TrackBack/1.02


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : wispr


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : EMPTY USER-AGENT STRING!


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : Mozilla/4.75 (Nikto/2.01)


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : curl/7.7.2 (powerpc-apple-darwin6.0) libcurl 7.7.2 (OpenSSL 0.9.6b)


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : w3af.sourceforge.net


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : HTTrack


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : Wget 1.9cvs-stable


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : Lynx (textmode)


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : .nasl


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : paros


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : webinspect


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : brutus


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : java


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : Googlebot/2.1 (+http://www.google.com/bot.html)


    [!] Data (MD5): f41863b91ca74b3926cf1da78d18d165


 [>] User-Agent String : Googlebot-Image/1.0


    [!] Data (MD5): 46fa90e6bc24d0399e3c17a2922636e6


 [>] User-Agent String : Mediapartners-Google


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : Mozilla/2.0 (compatible; Ask Jeeves)


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : msnbot-Products/1.0 (+http://search.msn.com/msnbot.htm)


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] User-Agent String : mmcrawler


    [!] Content-Type: text/html; charset=ISO-8859-1


 [>] That's all folks... Fo' Shizzle!
```

Links
-------
[UATester Google project](https://code.google.com/p/ua-tester/)
[InfoSec Daily Video](https://www.youtube.com/watch?v=mGuHks3Qb8I)

