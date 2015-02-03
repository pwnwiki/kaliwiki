# deblaze

Notes
-------

Help Text
-------
```
Usage: deblaze [option]

A remote enumeration tool for Flex Servers

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -u URL, --url=URL     URL for AMF Gateway
  -s SERVICE, --service=SERVICE
                        Remote service to call
  -m METHOD, --method=METHOD
                        Method to call
  -p PARAMS, --params=PARAMS
                        Parameters to send pipe seperated
                        'param1|param2|param3'
  -f SWF, --fullauto=SWF
                        URL to SWF - Download SWF, find remoting services,
                        methods,and parameters
  --fuzz                Fuzz parameter values
  -c CREDS, --creds=CREDS
                        Username and password for service in u:p format
  -b COOKIE, --cookie=COOKIE
                        Send cookies with request
  -A USERAGENT, --user-agent=USERAGENT
                        User-Agent string to send to the server
  -1 BRUTESERVICE, --bruteService=BRUTESERVICE
                        File to load services for brute forcing (mutually
                        exclusive to -s)
  -2 BRUTEMETHOD, --bruteMethod=BRUTEMETHOD
                        File to load methods for brute forcing (mutually
                        exclusive to -m)
  -d, --debug           Enable pyamf/AMF debugging
  -v, --verbose         Print http request/response
  -r, --report          Generate HTML report
  -n, --nobanner        Do not display banner
  -q, --quiet           Do not display messages

```

Example Usage
-------

Links
-------

