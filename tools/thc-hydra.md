# THC-Hydra

Notes
-------
A very fast and flexible network logon cracker which support many different services.


Help Text
-------
```
Hydra v7.6 (c)2013 by van Hauser/THC & David Maciejak - for legal purposes only

Syntax: hydra [[[-l LOGIN|-L FILE] [-p PASS|-P FILE]] | [-C FILE]] [-e nsr] [-o FILE] [-t TASKS] [-M FILE [-T TASKS]] [-w TIME] [-W TIME] [-f] [-s PORT] [-x MIN:MAX:CHARSET] [-SuvV46] [service://server[:PORT][/OPT]]

Options:
  -R        restore a previous aborted/crashed session
  -S        perform an SSL connect
  -s PORT   if the service is on a different default port, define it here
  -l LOGIN or -L FILE  login with LOGIN name, or load several logins from FILE
  -p PASS  or -P FILE  try password PASS, or load several passwords from FILE
  -x MIN:MAX:CHARSET  password bruteforce generation, type "-x -h" to get help
  -e nsr    try "n" null password, "s" login as pass and/or "r" reversed login
  -u        loop around users, not passwords (effective! implied with -x)
  -C FILE   colon separated "login:pass" format, instead of -L/-P options
  -M FILE   list of servers to be attacked in parallel, one entry per line
  -o FILE   write found login/password pairs to FILE instead of stdout
  -f / -F   exit when a login/pass pair is found (-M: -f per host, -F global)
  -t TASKS  run TASKS number of connects in parallel (per host, default: 16)
  -w / -W TIME  waittime for responses (32s) / between connects per thread
  -4 / -6   prefer IPv4 (default) or IPv6 addresses
  -v / -V / -d  verbose mode / show login+pass for each attempt / debug mode 
  -U        service module usage details
  server    the target server (use either this OR the -M option)
  service   the service to crack (see below for supported protocols)
  OPT       some service modules support additional input (-U for module help)

Supported services: asterisk afp cisco cisco-enable cvs firebird ftp ftps http[s]-{head|get} http[s]-{get|post}-form http-proxy http-proxy-urlenum icq imap[s] irc ldap2[s] ldap3[-{cram|digest}md5][s] mssql mysql ncp nntp oracle-listener oracle-sid pcanywhere pcnfs pop3[s] postgres rdp rexec rlogin rsh s7-300 sip smb smtp[s] smtp-enum snmp socks5 ssh sshkey svn teamspeak telnet[s] vmauthd vnc xmpp

Hydra is a tool to guess/crack valid login/password pairs - usage only allowed
for legal purposes. This tool is licensed under AGPL v3.0.
The newest version is always available at http://www.thc.org/thc-hydra
These services were not compiled in: sapr3 oracle.

Use HYDRA_PROXY_HTTP or HYDRA_PROXY - and if needed HYDRA_PROXY_AUTH - environment for a proxy setup.
E.g.:  % export HYDRA_PROXY=socks5://127.0.0.1:9150 (or socks4:// or connect://)
       % export HYDRA_PROXY_HTTP=http://proxy:8080
       % export HYDRA_PROXY_AUTH=user:pass

Examples:
  hydra -l user -P passlist.txt ftp://192.168.0.1
  hydra -L userlist.txt -p defaultpw imap://192.168.0.1/PLAIN
  hydra -C defaults.txt -6 pop3s://[fe80::2c:31ff:fe12:ac11]:143/TLS:DIGEST-MD5

```

Example Usage
-------

###HOW TO USE 
Stolen from Hydra's github [page](https://github.com/vanhauser-thc/thc-hydra/blob/master/README)

If you just enter `hydra`, you will see a short summary of the important
options available.
Type `./hydra -h` to see all available command line options.

Note that NO login/password file is included. Generate them yourself.
A default password list is hoever present, use `dpl4hydra.sh` to generate
a list.

For Linux users, a GTK gui is available, try `./xhydra`

For the command line usage, the syntax is as follows:
 For attacking one target or a network, you can use the new `://` style:
```  
  hydra [some command line options] PROTOCOL://TARGET:PORT/OPTIONS
```
 The old mode can be used for these too, and additionally if you want to
 specify your targets from a text file, you *must* use this one:
```
  hydra [some command line options] [-s port] TARGET PROTOCOL OPTIONS
```

Via the command line options you specify which logins to try, which passwords,
if SSL should be used, how many parallel tasks to use for attacking, etc.

PROTOCOL is the protocol you want to use for attacking, e.g. ftp, smtp,
http-get or many others are available
TARGET is the target you want to attack
OPTIONS are optional values which are special per PROTOCOL module

####FIRST - select your target
 you have three options on how to specify the target you want to attack:
 1. a single target on the command line: just put the IP or DNS address in
 2. a network range on the command line: CIDR specification like `192.168.0.0/24`
 3. a list of hosts in a text file: one line per entry (see below)

####SECOND - select your protocol
 Try to avoid telnet, as it is unreliable to detect a correct or false login attempt.
 Use a port scanner to see which protocols are enabled on the target.

####THIRD - check if the module has optional parameters
 `hydra -U PROTOCOL`
 e.g. `hydra -U smtp`

####FOURTH - the destination port
 this is optional! if no port is supplied the default common port for the
 PROTOCOL is used.
 If you specify SSL to use (`-S` option), the SSL common port is used by default.


If you use `://` notation, you must use `[` `]` brackets if you want to supply
IPv6 addresses or CIDR (`192.168.0.0/24`) notations to attack:
```
  hydra [some command line options] ftp://[192.168.0.0/24]/
  hydra [some command line options] -6 smtp://[2001:db8::1]/NTLM
```

Note that everything hydra does is IPv4 only!
If you want to attack IPv6 addresses, you must add the `-6` command line option.
All attacks are then IPv6 only!

If you want to supply your targets via a text file, you can not use the `://`
notation but use the old style and just supply the protocol (and module options):
```
  hydra [some command line options] -M targets.txt ftp
```

You can supply also port for each target entry by adding `:<port>` after a
target entry in the file, e.g.:
```
  foo.bar.com
  target.com:21
  unusual.port.com:2121
  default.used.here.com
  127.0.0.1
  127.0.0.1:2121
```

Note that if you want to attach IPv6 targets, you must supply the `-6` option
and *must* put IPv6 addresses in brackets in the file(!) like this:
```
  foo.bar.com
  target.com:21
  [fe80::1%eth0]
  [2001::1]
  [2002::2]:8080
  [2a01:24a:133:0:00:123:ff:1a]
```

###LOGINS AND PASSWORDS
--------------------
You have many options on how to attack with logins and passwords
With `-l` for login and `-p` for password you tell hydra that this is the only
login and/or password to try.
With `-L` for logins and `-P` for passwords you supply text files with entries.
e.g.:
```
  hydra -l admin -p password ftp://localhost/
  hydra -L default_logins.txt -p test ftp://localhost/
  hydra -l admin -P common_passwords.txt ftp://localhost/
  hydra -L logins.txt -P passwords.txt ftp://localhost/
```
Additionally, you can try passwords based on the login via the `-e` option.
The `-e` option has three parameters:
```
  s - try the login as password
  n - try an empty password
  r - reverse the login and try it as password
```

If you want to, e.g. try "try login as password and "empty password", you 
specify `-e sn` on the command line.


But there are two more modes for trying passwords than `-p`/`-P`:
You can use text file which where a login and password pair is seperated by a colon,
e.g.:
```
  admin:password
  test:test
  foo:bar
```

This is a common default account style listing, that is also generated by the
dpl4hydra.sh default account file generator supplied with hydra.
You use such a text file with the `-C` option - note that in this mode you
can not use `-l`/`-L`/`-p`/`-P` options (`-e` nsr however you can).
Example:
```
  hydra -C default_accounts.txt ftp://localhost/
```

And finally, there is a bruteforce mode with the -x option (which you can not
use with -p/-P/-C):
  `-x minimum_length:maximum_length:charset`
the charset definition is 'a' for lowercase letters, 'A' for uppercase letters,
'1' for numbers and for anything else you supply it is their real representation.
Examples:
```
  -x 1:3:a generate passwords from length 1 to 3 with all lowercase letters
  -x 2:5:/ generate passwords from length 2 to 5 containing only slashes
  -x 5:8:A1 generate passwords from length 5 to 8 with uppercase and numbers
```

Example:
```
  hydra -l ftp -x 3:3:a ftp://localhost/
```


###SPECIAL OPTIONS FOR MODULES
---------------------------
Via the third command line parameter (TARGET SERVICE OPTIONAL) or the `-m`
commandline option, you can pass one option to a module.
Many modules use this, a few require it!

To see the special option of a module, type:
```
  hydra -U <module>
```
e.g.
```
  ./hydra -U http-post-form
```

The special options can be passed via the -m parameter, as 3rd command line
option or in the `service://target/option` format.

Examples (they are all equal):
```
  ./hydra -l test -p test -m PLAIN 127.0.0.1 imap
  ./hydra -l test -p test 127.0.0.1 imap PLAIN
  ./hydra -l test -p test imap://127.0.0.1/PLAIN
```

Links
-------
[THC-Hydra minisite](https://www.thc.org/thc-hydra/)

[THC-Hydra Github project](https://github.com/vanhauser-thc/thc-hydra)
