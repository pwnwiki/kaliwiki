# fimap

Notes
-------

Help Text
-------
```
fimap v.09 (For the Swarm)
:: Automatic LFI/RFI scanner and exploiter
:: by Iman Karim (fimap.dev@gmail.com)

Usage: ./fimap.py [options]
## Operating Modes:
   -s , --single                 Mode to scan a single URL for FI errors.
                                 Needs URL (-u). This mode is the default.
   -m , --mass                   Mode for mass scanning. Will check every URL
                                 from a given list (-l) for FI errors.
   -g , --google                 Mode to use Google to aquire URLs.
                                 Needs a query (-q) as google search query.
   -H , --harvest                Mode to harvest a URL recursivly for new URLs.
                                 Needs a root url (-u) to start crawling there.
                                 Also needs (-w) to write a URL list for mass mode.
   -4 , --autoawesome            With the AutoAwesome mode fimap will fetch all
                                 forms and headers found on the site you defined
                                 and tries to find file inclusion bugs thru them. Needs an
                                 URL (-u).
## Techniques:
   -b , --enable-blind           Enables blind FI-Bug testing when no error messages are printed.
                                 Note that this mode will cause lots of requests compared to the
                                 default method. Can be used with -s, -m or -g.
   -D , --dot-truncation         Enables dot truncation technique to get rid of the suffix if
                                 the default mode (nullbyte poison) failed. This mode can cause
                                 tons of requests depending how you configure it.
                                 By default this mode only tests windows servers.
                                 Can be used with -s, -m or -g. Experimental.
   -M , --multiply-term=X        Multiply terminal symbols like '.' and '/' in the path by X.
## Variables:
   -u , --url=URL                The URL you want to test.
                                 Needed in single mode (-s).
   -l , --list=LIST              The URL-LIST you want to test.
                                 Needed in mass mode (-m).
   -q , --query=QUERY            The Google Search QUERY.
                                 Example: 'inurl:include.php'
                                 Needed in Google Mode (-g)
        --skip-pages=X           Skip the first X pages from the Googlescanner.
   -p , --pages=COUNT            Define the COUNT of pages to search (-g).
                                 Default is 10.
        --results=COUNT          The count of results the Googlescanner should get per page.
                                 Possible values: 10, 25, 50 or 100(default).
        --googlesleep=TIME       The time in seconds the Googlescanner should wait befor each
                                 request to google. fimap will count the time between two requests
                                 and will sleep if it's needed to reach your cooldown. Default is 5.
   -w , --write=LIST             The LIST which will be written if you have choosen
                                 harvest mode (-H). This file will be opened in APPEND mode.
   -d , --depth=CRAWLDEPTH       The CRAWLDEPTH (recurse level) you want to crawl your target site
                                 in harvest mode (-H). Default is 1.
   -P , --post=POSTDATA          The POSTDATA you want to send. All variables inside
                                 will also be scanned for file inclusion bugs.
        --cookie=COOKIES         Define the cookie which should be send with each request.
                                 Also the cookies will be scanned for file inclusion bugs.
                                 Concatenate multiple cookies with the ';' character.
        --ttl=SECONDS            Define the TTL (in seconds) for requests. Default is 30 seconds.
        --no-auto-detect         Use this switch if you don't want to let fimap automaticly detect
                                 the target language in blind-mode. In that case you will get some
                                 options you can choose if fimap isn't sure which lang it is.
        --bmin=BLIND_MIN         Define here the minimum count of directories fimap should walk thru
                                 in blind mode. The default number is defined in the generic.xml
        --bmax=BLIND_MAX         Define here the maximum count of directories fimap should walk thru.
        --dot-trunc-min=700      The count of dots to begin with in dot-truncation mode.
        --dot-trunc-max=2000     The count of dots to end with in dot-truncation mode.
        --dot-trunc-step=50      The step size for each round in dot-truncation mode.
        --dot-trunc-ratio=0.095  The maximum ratio to detect if dot truncation was successfull.
        --dot-trunc-also-unix    Use this if dot-truncation should also be tested on unix servers.
        --force-os=OS            Forces fimap to test only files for the OS.
                                 OS can be 'unix' or 'windows'
## Attack Kit:
   -x , --exploit                Starts an interactive session where you can
                                 select a target and do some action.
   -T , --tab-complete           Enables TAB-Completation in exploit mode. Needs readline module.
                                 Use this if you want to be able to tab-complete thru remote
                                 files\dirs. Eats an extra request for every 'cd' command.
## Disguise Kit:
   -A , --user-agent=UA          The User-Agent which should be sent.
        --http-proxy=PROXY       Setup your proxy with this option. But read this facts:
                                   * The googlescanner will ignore the proxy to get the URLs,
                                     but the pentest\attack itself will go thru proxy.
                                   * PROXY should be in format like this: 127.0.0.1:8080
                                   * It's experimental
        --show-my-ip             Shows your internet IP, current country and user-agent.
                                 Useful if you want to test your vpn\proxy config.
## Plugins:
        --plugins                List all loaded plugins and quit after that.
   -I , --install-plugins        Shows some official exploit-mode plugins you can install 
                                 and\or upgrade.
## Other:
        --update-def             Checks and updates your definition files found in the
                                 config directory.
        --test-rfi               A quick test to see if you have configured RFI nicely.
        --merge-xml=XMLFILE      Use this if you have another fimap XMLFILE you want to
                                 include to your own fimap_result.xml.
   -C , --enable-color           Enables a colorful output. Works only in linux!
        --force-run              Ignore the instance check and just run fimap even if a lockfile
                                 exists. WARNING: This may erase your fimap_results.xml file!
   -v , --verbose=LEVEL          Verbose level you want to receive.
                                 LEVEL=3 -> Debug
                                 LEVEL=2 -> Info(Default)
                                 LEVEL=1 -> Messages
                                 LEVEL=0 -> High-Level
        --credits                Shows some credits.
        --greetings              Some greetings ;)
   -h , --help                   Shows this cruft.
## Examples:
  1. Scan a single URL for FI errors:
        ./fimap.py -u 'http://localhost/test.php?file=bang&id=23'
  2. Scan a list of URLS for FI errors:
        ./fimap.py -m -l '/tmp/urllist.txt'
  3. Scan Google search results for FI errors:
        ./fimap.py -g -q 'inurl:include.php'
  4. Harvest all links of a webpage with recurse level of 3 and
     write the URLs to /tmp/urllist
        ./fimap.py -H -u 'http://localhost' -d 3 -w /tmp/urllist

```

Example Usage
-------

Links
-------

