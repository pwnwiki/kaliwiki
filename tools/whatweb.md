# whatweb

Notes
-------

Help Text
-------
```
.$$$     $.                                   .$$$     $.         
$$$$     $$. .$$$  $$$ .$$$$$$.  .$$$$$$$$$$. $$$$     $$. .$$$$$$$. .$$$$$$. 
$ $$     $$$ $ $$  $$$ $ $$$$$$. $$$$$ $$$$$$ $ $$     $$$ $ $$   $$ $ $$$$$$.
$ `$     $$$ $ `$  $$$ $ `$  $$$ $$' $ `$ `$$ $ `$     $$$ $ `$      $ `$  $$$'
$. $     $$$ $. $$$$$$ $. $$$$$$ `$  $. $  :' $. $     $$$ $. $$$$   $. $$$$$.
$::$  .  $$$ $::$  $$$ $::$  $$$     $::$     $::$  .  $$$ $::$      $::$  $$$$
$;;$ $$$ $$$ $;;$  $$$ $;;$  $$$     $;;$     $;;$ $$$ $$$ $;;$      $;;$  $$$$
$$$$$$ $$$$$ $$$$  $$$ $$$$  $$$     $$$$     $$$$$$ $$$$$ $$$$$$$$$ $$$$$$$$$'

WhatWeb - Next generation web scanner.
Version 0.4.8-dev by Andrew Horton aka urbanadventurer
Homepage: http://www.morningstarsecurity.com/research/whatweb

Usage: whatweb [options] <URLs>

TARGET SELECTION:
  <URLs>		Enter URLs, filenames or nmap-format IP ranges.
			Use /dev/stdin to pipe HTML directly
  --input-file=FILE, -i	Identify URLs found in FILE, eg. -i /dev/stdin

TARGET MODIFICATION:
  --url-prefix		Add a prefix to target URLs
  --url-suffix		Add a suffix to target URLs
  --url-pattern		Insert the targets into a URL. Requires --input-file,
			eg. www.example.com/%insert%/robots.txt 

AGGRESSION:
  The aggression level controls the trade-off between speed/stealth and
  reliability.
  --aggression, -a=LEVEL Set the aggression level. Default: 1
  Aggression levels are:
  1. Stealthy	Makes one HTTP request per target. Also follows redirects.
  2. Unused
  3. Aggressive	Can make a handful of HTTP requests per target. This triggers
  		aggressive plugins for targets only when those plugins are
  		identified with a level 1 request first.
  4. Heavy	Makes a lot of HTTP requests per target. Aggressive tests from
  		all plugins are used for all URLs.

HTTP OPTIONS:
  --user-agent, -U=AGENT Identify as AGENT instead of WhatWeb/0.4.8-dev.
  --header, -H		Add an HTTP header. eg "Foo:Bar". Specifying a default
			header will replace it. Specifying an empty value, eg.
			"User-Agent:" will remove the header.
  --follow-redirect=WHEN Control when to follow redirects. WHEN may be `never',
			`http-only', `meta-only', `same-site', `same-domain'
			or `always'. Default: always
  --max-redirects=NUM	Maximum number of contiguous redirects. Default: 10

AUTHENTICATION:
  --user, -u=<user:password> HTTP basic authentication
  Add session cookies with --header, e.g. --header "Cookie: SESSID=1a2b3c;"

PROXY:
  --proxy		<hostname[:port]> Set proxy hostname and port
			Default: 8080
  --proxy-user		<username:password> Set proxy user and password

PLUGINS:
  --list-plugins, -l	List all plugins
  --plugins, -p=LIST	Select plugins. LIST is a comma delimited set of 
			selected plugins. Default is all.
			Each element can be a directory, file or plugin name and
			can optionally have a modifier, eg. + or -
			Examples: +/tmp/moo.rb,+/tmp/foo.rb
			title,md5,+./plugins-disabled/
			./plugins-disabled,-md5
			-p + is a shortcut for -p +plugins-disabled
  --info-plugins, -I=PLUGINS	Display detailed information for plugins.
			Optionally search with keywords in a comma delimited
			list.
  --grep, -g=STRING	Search for STRING in HTTP responses. Reports with a
			plugin named Grep
  --custom-plugin=DEFINITION	Define a custom plugin named Custom-Plugin,
			Examples: ":text=>'powered by abc'"
			":version=>/powered[ ]?by ab[0-9]/"
			":ghdb=>'intitle:abc \"powered by abc\"'"
			":md5=>'8666257030b94d3bdb46e05945f60b42'"
			"{:text=>'powered by abc'},{:regexp=>/abc [ ]?1/i}"
  --dorks=PLUGIN	List google dorks for the selected plugin
  --example-urls, -e=PLUGIN Update the target list with example URLs from
			the selected plugins.

OUTPUT:
  --verbose, -v		Verbose output includes plugin descriptions. Use twice
			for debugging.
  --colour,--color=WHEN	control whether colour is used. WHEN may be `never',
			`always', or `auto'
  --quiet, -q		Do not display brief logging to STDOUT
  --no-errors		Suppress error messages

LOGGING:
  --log-brief=FILE	Log brief, one-line output
  --log-verbose=FILE	Log verbose output
  --log-xml=FILE	Log XML format
  --log-json=FILE	Log JSON format
  --log-json-verbose=FILE Log JSON Verbose format
  --log-magictree=FILE	Log MagicTree XML format
  --log-object=FILE	Log Ruby object inspection format
  --log-mongo-database	Name of the MongoDB database
  --log-mongo-collection Name of the MongoDB collection. Default: whatweb
  --log-mongo-host	MongoDB hostname or IP address. Default: 0.0.0.0
  --log-mongo-username	MongoDB username. Default: nil
  --log-mongo-password	MongoDB password. Default: nil
  --log-errors=FILE	Log errors

PERFORMANCE & STABILITY:
  --max-threads, -t	Number of simultaneous threads. Default: 25.
  --open-timeout	Time in seconds. Default: 15
  --read-timeout	Time in seconds. Default: 30
  --wait=SECONDS	Wait SECONDS between connections
			This is useful when using a single thread.

HELP & MISCELLANEOUS:
  --help, -h		This help
  --debug		Raise errors in plugins
  --version		Display version information. (WhatWeb 0.4.8-dev)

EXAMPLE USAGE:
* Scan example.com
  whatweb example.com
* Scan reddit.com slashdot.org with verbose plugin descriptions
  whatweb -v reddit.com slashdot.org
* An aggressive scan of mashable.com detects the exact version of Wordpress
  whatweb -a 3 mashable.com
* Scan the local network quickly with 255 threads and suppress errors
  whatweb --no-errors -t 255 192.168.0.0/24

OPTIONAL DEPENDENCIES
--------------------------------------------------------------------------------
To enable MongoDB logging install the mongo gem.

WARNING: Ruby 1.9 support is experimental. For stable usage use Ruby 1.8 instead. Please report bugs at https://github.com/urbanadventurer/WhatWeb/issue

```

Example Usage
-------

Links
-------

