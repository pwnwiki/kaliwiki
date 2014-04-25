# wapti

Notes
-------

Help Text
-------
```
Wapiti-SVN - A web application vulnerability scanner 
 
 Usage: python wapiti.py http://server.com/base/url/ [options] 
 
 Supported options are: 
 -s <url> 
 --start <url> 
 	To specify an url to start with 
  
 -x <url> 
 --exclude <url> 
 	To exclude an url from the scan (for example logout scripts) 
 	You can also use a wildcard (*) 
 	Example : -x http://server/base/?page=*&module=test 
 	or -x http://server/base/admin/* to exclude a directory 
 
 -p <url_proxy> 
 --proxy <url_proxy> 
 	To specify a proxy 
 	Example: -p http://proxy:port/ 
 
 -c <cookie_file> 
 --cookie <cookie_file> 
 	To use a cookie 
 
 -t <timeout> 
 --timeout <timeout> 
 	To fix the timeout (in seconds) 
 
 -a <login%password> 
 --auth <login%password> 
 	Set credentials for HTTP authentication 
 	Doesn't work with Python 2.4 
 
 -r <parameter_name> 
 --remove <parameter_name> 
 	Remove a parameter from URLs 
 
 -n <limit> 
 --nice <limit> 
 	Define a limit of urls to read with the same pattern 
 	Use this option to prevent endless loops 
 	Must be greater than 0 
 
-m <module_options>
--module <module_options>
	Set the modules and HTTP methods to use for attacks.
	Example: -m "-all,xss:get,exec:post"
 
 -u 
 --underline 
 	Use color to highlight vulnerables parameters in output 
 
 -v <level> 
 --verbose <level> 
 	Set the verbosity level 
 	0: quiet (default), 1: print each url, 2: print every attack 
 
 -b <scope>
 --scope <scope>
 	Set the scope of the scan:
 		+ "page":  to analyse only the page passed in the URL
 		+ "folder":to analyse all the links to the pages which are in the same folder as the URL passed to Wapiti.
 		+ "domain":to analyse all the links to the pages which are in the same domain as the URL passed to Wapiti.
 	If no scope is set, Wapiti scans all the tree under the given URL.
 
 -f <type_file> 
 --reportType <type_file> 
 	Set the type of the report 
 	xml: Report in XML format 
 	html: Report in HTML format 
 	txt: Report in plain text 
 
 -o <output> 
 --output <output_file> 
 	Set the name of the report file 
 	If the selected report type is 'html', this parameter must be a directory 
 
 -i <file>
 --continue <file>
 	This parameter indicates Wapiti to continue with the scan from the specified file, this file should contain data from a previous scan.
 	The file is optional, if it is not specified, Wapiti takes the default file from the "scans" folder.
 
 -k <file>
 --attack <file>
 	This parameter indicates Wapiti to perform attacks without scanning again the website and following the data of this file.
 	The file is optional, if it is not specified, Wapiti takes the default file from the "scans" folder.
 
 -h 
 --help 
 	To print this usage message

```

Example Usage
-------

Links
-------

