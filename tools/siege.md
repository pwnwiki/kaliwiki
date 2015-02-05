# siege

Notes
-------
Siege is a regression test and benchmark utility. 
It can stress test a single URL with a user defined number of simulated users, or it can read many URLs into memory and stress them simultaneously. 
The program reports the total number of hits recorded, bytes transferred, response time, concurrency, and return status. 
Siege supports HTTP/1.0 and 1.1 protocols, GET and POST directives, cookies, transaction logging, and basic authentication.
Its features are configurable on a per user basis. 


Help Text
-------
```
SIEGE 3.0.5
Usage: siege [options]
       siege [options] URL
       siege -g URL
Options:
  -V, --version             VERSION, prints the version number.
  -h, --help                HELP, prints this section.
  -C, --config              CONFIGURATION, show the current config.
  -v, --verbose             VERBOSE, prints notification to screen.
  -q, --quiet               QUIET turns verbose off and suppresses output.
  -g, --get                 GET, pull down HTTP headers and display the
                            transaction. Great for application debugging.
  -c, --concurrent=NUM      CONCURRENT users, default is 10
  -i, --internet            INTERNET user simulation, hits URLs randomly.
  -b, --benchmark           BENCHMARK: no delays between requests.
  -t, --time=NUMm           TIMED testing where "m" is modifier S, M, or H
                            ex: --time=1H, one hour test.
  -r, --reps=NUM            REPS, number of times to run the test.
  -f, --file=FILE           FILE, select a specific URLS FILE.
  -R, --rc=FILE             RC, specify an siegerc file
  -l, --log[=FILE]          LOG to FILE. If FILE is not specified, the
                            default is used: /var/siege.log
  -m, --mark="text"         MARK, mark the log file with a string.
  -d, --delay=NUM           Time DELAY, random delay before each requst
                            between 1 and NUM. (NOT COUNTED IN STATS)
  -H, --header="text"       Add a header to request (can be many)
  -A, --user-agent="text"   Sets User-Agent in request
  -T, --content-type="text" Sets Content-Type in request

Copyright (C) 2013 by Jeffrey Fulmer, et al.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS
FOR A PARTICULAR PURPOSE
```

Example Usage
-------


```

```

Links
-------
[Siege Homepage](http://www.joedog.org/siege-home/)

[Siege Freecode project](http://freecode.com/projects/siege)
