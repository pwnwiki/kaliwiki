# john (john the ripper)

Notes
-------
John the Ripper is a fast password cracker, currently available for many flavors of Unix, Windows, DOS, BeOS, and OpenVMS. Its primary purpose is to detect weak Unix passwords. Besides several crypt(3) password hash types most commonly found on various Unix systems, supported out of the box are Windows LM hashes, plus lots of other hashes and ciphers in the community-enhanced version.

To use John, you just need to supply it a password file and the desired options.  If  no  mode is specified, john will try "single" first, then "wordlist" and finally "incremental".

Once John finds a password, it will be  printed  to  the  terminal  and saved  into  a  file  called ~/.john/john.pot. John will read this file when it restarts so it doesn't try to crack already done passwords. 

To see the cracked passwords, use

```
john -show passwd
```

Important: do this under the same  directory  where  the  password  was cracked  (when  using  the  cronjob, /var/lib/john), otherwise it won't
 
While cracking, you can press any key for status, or  Ctrl+C  to  abort the  session,  saving point information to a file ( ~/.john/john.rec by default). By the way, if you press Ctrl+C twice John will abort immediately  without  saving.   The  point information is also saved every 10 minutes (configurable in the configuration  file,  ~/.john/john.ini  or ~/.john/john.conf ) in case of a crash.

To continue an interrupted session, run:

```
john -restore
```

Now,  you  may notice that many accounts have a disabled shell, you can make John ignore these (assume that shell is called /etc/expired ):

```
john -show -shells:-/etc/expired passwd
```

You might want to mail all the users who got weak  passwords,  to  tell them  to  change  the  passwords.  It's  not  always a good idea though (unfortunately, lots of people seem to ignore such mail, it can be used as  a  hint  for  crackers, etc), but anyway, I'll assume you know what you're doing. Get a copy of the 'mailer' script supplied with John,  so you  won't change anything that's under /usr/sbin ; edit the message it sends, and possibly the mail command inside it (especially if the password  file is from a different box than you got John running on).  Then run:

```
 ./mailer passwd
```
 
Anyway, you probably should have a look at  /usr/share/doc/john/OPTIONS for    a   list   of   all   the   command   line   options,   and   at /usr/share/doc/john/EXAMPLES for more John usage  examples  with  other cracking modes.


Help Text
-------
```
John the Ripper password cracker, ver: 1.7.9-jumbo-7_omp [linux-x86-64]
Copyright (c) 1996-2012 by Solar Designer and others
Homepage: http://www.openwall.com/john/

Usage: john [OPTIONS] [PASSWORD-FILES]
--config=FILE             use FILE instead of john.conf or john.ini
--single[=SECTION]        "single crack" mode
--wordlist[=FILE] --stdin wordlist mode, read words from FILE or stdin
                  --pipe  like --stdin, but bulk reads, and allows rules
--loopback[=FILE]         like --wordlist, but fetch words from a .pot file
--dupe-suppression        suppress all dupes in wordlist (and force preload)
--encoding=NAME           input data is non-ascii (eg. UTF-8, ISO-8859-1).
                          For a full list of NAME use --list=encodings
--rules[=SECTION]         enable word mangling rules for wordlist modes
--incremental[=MODE]      "incremental" mode [using section MODE]
--markov[=OPTIONS]        "Markov" mode (see doc/MARKOV)
--external=MODE           external mode or word filter
--stdout[=LENGTH]         just output candidate passwords [cut at LENGTH]
--restore[=NAME]          restore an interrupted session [called NAME]
--session=NAME            give a new session the NAME
--status[=NAME]           print status of a session [called NAME]
--make-charset=FILE       make a charset file. It will be overwritten
--show[=LEFT]             show cracked passwords [if =LEFT, then uncracked]
--test[=TIME]             run tests and benchmarks for TIME seconds each
--users=[-]LOGIN|UID[,..] [do not] load this (these) user(s) only
--groups=[-]GID[,..]      load users [not] of this (these) group(s) only
--shells=[-]SHELL[,..]    load users with[out] this (these) shell(s) only
--salts=[-]COUNT[:MAX]    load salts with[out] COUNT [to MAX] hashes
--pot=NAME                pot file to use
--format=NAME             force hash type NAME: afs bf bfegg bsdi crc32 crypt
                          des django dmd5 dominosec dragonfly3-32 dragonfly3-64
                          dragonfly4-32 dragonfly4-64 drupal7 dummy dynamic_n
                          epi episerver gost hdaa hmac-md5 hmac-sha1
                          hmac-sha224 hmac-sha256 hmac-sha384 hmac-sha512
                          hmailserver ipb2 keepass keychain krb4 krb5 lm lotus5
                          md4-gen md5 md5ns mediawiki mscash mscash2 mschapv2
                          mskrb5 mssql mssql05 mysql mysql-sha1 nethalflm netlm
                          netlmv2 netntlm netntlmv2 nsldap nt nt2 odf office
                          oracle oracle11 osc pdf phpass phps pix-md5 pkzip po
                          pwsafe racf rar raw-md4 raw-md5 raw-md5u raw-sha
                          raw-sha1 raw-sha1-linkedin raw-sha1-ng raw-sha224
                          raw-sha256 raw-sha384 raw-sha512 salted-sha1 sapb
                          sapg sha1-gen sha256crypt sha512crypt sip ssh
                          sybasease trip vnc wbb3 wpapsk xsha xsha512 zip
--list=WHAT               list capabilities, see --list=help or doc/OPTIONS
--save-memory=LEVEL       enable memory saving, at LEVEL 1..3
--mem-file-size=SIZE      size threshold for wordlist preload (default 5 MB)
--nolog                   disables creation and writing to john.log file
--crack-status            emit a status line whenever a password is cracked
--max-run-time=N          gracefully exit after this many seconds
--regen-lost-salts=N      regenerate lost salts (see doc/OPTIONS)
--plugin=NAME[,..]        load this (these) dynamic plugin(s)
how to launch the tool
```

Example Usage
-------
Very simple john usage to crack unshadowed passwords with rockyou.txt--located in /usr/bin/wordlists:

```
# john --wordlist=/usr/share/wordlists/rockyou.txt ./unshadow.txt
```

Examples from [FAQ](http://www.openwall.com/john/doc/EXAMPLES.shtml):
1. First, you need to get a copy of your password file. If your system uses shadow passwords, you may use John's "unshadow" utility to obtain the traditional Unix password file, as root:

```
	umask 077
	unshadow /etc/passwd /etc/shadow > mypasswd
```
	
(You may need to replace the filenames as needed.)

Then make "mypasswd" available to your non-root user account that you will run John under. No further commands will need to be run as root.

If your system is ancient enough that it keeps passwords right in the world-readable /etc/passwd, simply make a copy of that file.

If you're going to be cracking Kerberos AFS passwords, use John's "unafs" utility to obtain a passwd-like file.

Similarly, if you're going to be cracking Windows passwords, use any of the many utilities that dump Windows password hashes (LM and/or NTLM) in Jeremy Allison's PWDUMP output format. Some of these utilities may be obtained here:

	http://www.openwall.com/passwords/pwdump
2. Now, let's assume you've got a password file, "mypasswd", and want to crack it. The simplest way is to let John use its default order of cracking modes:

```
	john mypasswd
```
	
This will try "single crack" mode first, then use a wordlist with rules, and finally go for "incremental" mode. Please refer to MODES for more information on these modes.

It is highly recommended that you obtain a larger wordlist than John's default password.lst and edit the "Wordlist = ..." line in the configuration file (see CONFIG) before running John. Some wordlists may be obtained here:

	http://www.openwall.com/wordlists/
Of those available in the collection at the URL above, all.lst (downloadable as all.gz) and huge.lst (only available on the CD) are good candidates for the "Wordlist = ..." setting.

3. If you've got some passwords cracked, they are stored in $JOHN/john.pot. The john.pot file is not meant to be human-friendly. You should be using John itself to display the contents of its "pot file" in a convenient format:

```
	john --show mypasswd
```	
	
If the account list gets large and doesn't fit on the screen, you should, of course, use your shell's output redirection.

You might notice that many accounts have a disabled shell. You can make John skip those in the report. Assuming that the disabled shell is called "/etc/expired", the command would be:

```
	john --show --shells=-/etc/expired mypasswd
```
	
or shorter, but will also match "/any/path/expired":

```
	john --show --shells=-expired mypasswd
```	
	
or if you also want to ignore some other shell, say "/etc/newuser":

```
	john --show --shells=-expired,newuser mypasswd
```	
	
To check if any root (UID 0) accounts got cracked:

```
	john --show --users=0 mypasswd
```
	
or to check for cracked root (UID 0) accounts in multiple files:

```
	john --show --users=0 *passwd* *.pwd
```	
	
To display the root (username "root") account only:

```
	john --show --users=root mypasswd
```
	
And finally, to check for privileged groups:

```
	john --show --groups=0,1 mypasswd
```	
	
4. You might prefer to manage the cracking modes manually. It is wise to start with "single crack" mode:

```
	john --single mypasswd
```	
	
or since the GNU-style double dashes are optional and since option names can be abbreviated for as long as they remain unambiguous:

```
	john -si mypasswd
```	
	
You should not abbreviate options in scripts which you would want to work with future versions of John since what is unambiguous now might become ambiguous with the addition of more options.

If you have more files to crack, it is preferable to load them at the same time:

```
	john --single passwd1 passwd2
```	
	
or even:

```
	john --single *passwd* *.pwd
```	
	
This way, John will run faster and might even crack more passwords than it would if you ran it on each password file separately.

5. To catch weak passwords not derived from readily available users' personal information, you should proceed with cracking modes demanding more processor time. First, let's try a tiny wordlist with word mangling rules enabled:

```
	john --wordlist=password.lst --rules mypasswd	
```
	
or abbreviating the options:

```
	john -w=password.lst -ru mypasswd
```

Then proceed with a larger wordlist, also applying the mangling rules:

```
	john --wordlist=all.lst --rules mypasswd
```

If you've got a lot of spare disk space to trade for performance and the hash type of your password files is relatively slow, you may use John's "unique" utility to eliminate any duplicate candidate passwords:

```
	john --wordlist=all.lst --rules --stdout | unique mangled.lst
	john --wordlist=mangled.lst mypasswd
```	
	
If you know that your target hash type truncates passwords at a given length, you may optimize this even further:

```
	john --wordlist=all.lst --rules --stdout=8 | unique mangled8.lst
	john --wordlist=mangled8.lst mypasswd
```	
	
Alternatively, you may simply use huge.lst available on Openwall wordlist collection CDs. It has word mangling rules pre-applied for the most common languages and it has any duplicates purged.

Depending on target hash type, the number of different salts (if applicable), the size of your wordlist, rules, and processor performance, wordlist-based cracking may take anywhere from under a second to many days.

You do not have to leave John running on a (pseudo-)terminal. If running John on a Unix-like system, you can simply disconnect from the server, close your xterm, etc. John will catch the SIGHUP ("hangup" signal) and continue running. Alternatively, you may prefer to start it in the background right away:

```
	john --wordlist=all.lst --rules mypasswd &
```
	
Obviously, the "&" is specific to Unix shells and will not work on most other platforms.

You may further enhance this by specifying a session name:

```
	john --session=allrules --wordlist=all.lst --rules mypasswd &
```
	
This ensures that you won't accidentally interfere with the instance of John running in the background if you proceed to start other sessions.

To view the status of a running session, use:

```
	john --status
```
	
for the default session or:

```
	john --status=allrules
```
	
for any other session. This works for both interrupted and running sessions. To obtain the most up-to-date information from a running session on a Unix-like system, send a SIGHUP to the appropriate "john" process.

Any interrupted sessions may be continued with:

```
	john --restore
```
	
or:

```
	john --restore=allrules
```
	
Finally, to make John have less impact on other processes, you should set the option "Idle = Y" in the configuration file (see CONFIG). The default may vary depending on the version and build of JtR.

To only crack accounts with a "good" shell (in general, the shell, user, and group filters described above work for all cracking modes as well):

```
	john --wordlist=all.lst --rules --shells=sh,csh,tcsh,bash mypasswd
```
	
Like with all other cracking modes, it is faster to crack all the files you need cracked simultaneously:

```
	john --wordlist=all.lst --rules passwd1 passwd2
```

	You can crack some passwords only. This will try cracking all root (UID 0) accounts in all the password files:

```
	john --wordlist=all.lst --rules --users=0 *passwd*
```

Alternatively, you may wish to not waste time cracking your very own passwords, if you're sure they're uncrackable:

```
	john --wordlist=all.lst --rules --users=-root,solar *passwd*
```

Sometimes it is useful to split your password hashes into two sets which you crack separately, like:

```
	john --wordlist=all.lst --rules --salts=2 *passwd*
	john --wordlist=all.lst --rules --salts=-2 *passwd*
```

This will make John try salts used on two or more password hashes first and then try the rest. Total cracking time will be almost the same, but you will get some passwords cracked earlier, which is useful, for example, for penetration testing and demonstrations to management. Similarly, you may check all password hashes with a small wordlist, but only those that you can check faster (with "--salts=2") with a larger one. With large numbers of password hashes and/or with a highly non-uniform distribution of salts, it may be appropriate to use a threshold larger than 2 with "--salts" (sometimes even values as high as 1000 will do).

Note that the default wordlist rules include ":" (a no-op - try words as they are in the list) on the first line. If you already ran through a wordlist without using rules, and then decided to also try the same wordlist with rules, you'd better comment this line out.

6. The most powerful cracking mode in John is called "incremental" (not a proper name, but kept for historical reasons). You can simply run:

```
	john --incremental mypasswd
```

or:

```
	john -i mypasswd
```
	
This will use the default "incremental" mode parameters, which are defined in the configuration file's section named either [Incremental:ASCII] (for most hash types) or [Incremental:LM_ASCII] (for Windows LM hashes). By default, the [Incremental:ASCII] parameters are set to use the full printable ASCII character set (95 characters) and to try all possible password lengths from 0 to 13 (if the current hash type has a lower maximum password length, incremental mode's length limit is reduced accordingly). [Incremental:LM_ASCII] is similar, except that it takes advantage of LM hashes being case-insensitive and of their halves being limited to 7 characters each.

Don't expect "incremental" mode sessions to terminate in a reasonable time (unless all the passwords are weak and get cracked), read MODES for an explanation of this.

In some cases it is faster to use some other pre-defined incremental mode parameters and only crack simpler passwords, from a limited character set. The following command will try 10 different characters only, passwords from "0" to "99999999999999999999" (in an optimal order):

```
	john -i=digits mypasswd
```	

Of course, you can use most of the additional features demonstrated above for wordlist mode with "incremental" mode as well. For example, on a large-scale penetration test, you may have John crack only root (UID 0) accounts in a set of password files:

```
	john -i -u=0 *.pwd
```	

7. If you've got a password file for which you already have a lot of passwords cracked or obtained by other means, and the passwords are unusual, then you may want to generate a new charset file, based on character frequencies from that password file only:

```
	john --make-charset=custom.chr mypasswd
```	

Then use that new file with "incremental" mode.

If you've got many password files from a particular country, organization, etc., it might be useful to use all of them for the charset file that you then use to crack even more passwords from these files or from some other password files from the same place:

```
	john --make-charset=custom.chr passwd1 passwd2
	[ Configure your custom "incremental" mode now. See below. ]
	john -i=custom passwd3
```

You can use some pre-defined or custom word filters when generating the charset file to have John consider some simpler passwords only:

```
	john --make-charset=my_alpha.chr --external=filter_alpha mypasswd
```

If your "pot file" got large enough (or if you don't have any charset files at all), you might want to use it to generate a new set of main charset files:

```
	makechr
```

where "makechr" is a script that invokes "john --make-charset=..." with varying filenames, for all of the external mode word filters defined in the configuration file. In this example, John will overwrite the charset files with new ones that are based on your entire $JOHN/john.pot (John uses the entire "pot file" if you don't specify any password files).

8. Finally, you might want to e-mail all users with weak passwords to tell them to change their passwords. (This is not always a good idea, though, since lots of people do not check their e-mail or ignore such messages, and the messages can be a hint for crackers.) Edit the "mailer" script supplied with John: the message it sends and possibly the mail command (especially if the password file is from a different machine). Then run:

```
	mailer mypasswd
```


Example found on [john wiki](http://openwall.info/wiki/john/tutorials/sha-crypt):

Date: Sun, 20 Jun 2010 21:09:39 +0400
From: Solar Designer <solar@...nwall.com>
To: john-users@...ts.openwall.com
Subject: auditing SHA-crypt hashes with JtR 1.7.6+ on Linux (Ubuntu, Fedora, etc.), including OpenMP parallelization

Hi,

Earlier today, I posted a tutorial on auditing SHA-crypt hashes on
Solaris 10:

http://www.openwall.com/lists/john-users/2010/06/20/2

The following is a similar tutorial for doing it on Linux.  (In fact, I
am posting to the same thread to make it easy to find this new tutorial
for those who happen to find the previous posting first.)

I'll be using Fedora 12 on x86-64.  (More specifically, this is an
OpenVZ container on Openwall GNU/*/Linux, instantiated from
fedora-12-x86_64.tar.gz, which was downloaded from
http://download.openvz.org/template/precreated/ , with gcc installed
into it with "yum install gcc" as root.)  The machine uses a Core i7 920
CPU at 2.66 GHz (with Turbo Boost to a higher frequency when only 1 or 2
CPU cores are in use).

Here's the version of gcc:

```
[solar@...ora12 ~]$ rpm -q gcc
gcc-4.4.3-4.fc12.x86_64
[solar@...ora12 ~]$ gcc -v 2>&1 | tail -1
gcc version 4.4.3 20100127 (Red Hat 4.4.3-4) (GCC)
```

This one is OpenMP-capable (must be 4.2 or newer), which we'll make use
of further down this tutorial.

The password file looks like:

```
[solar@...ora12 john]$ cat pw-sha-rs904c 
test:$6$MDZEL9CQ$ZentsLbLWphRB2./B0xKv1vWPY9IBknYrcD.3SlY5RamKsnzlCSC4ImT3KWY8rXMbodbFA9wDrlf51DT3HgoW1:102:14::/home/test:/bin/sh
test:$6$dofn/L59$nygYCacync7RzPfYjWZ1OO6b8MZDETUzYP2SbJD0PPqXDjQ3caVlR8/O6G2DSMh.6X0Dzwre86QPifkEU22dW/:102:14::/home/test:/bin/sh
robert:$6$U4dzp4gvMho3$hAUA8cpTUdHnNjuMFUtiXzd0NL85RMNihshXdks/7LD5zDVseUawK1JIotk5JVZoyacpHy.Vuja0b9GD2gZ0J.:14527:0:99999:7:::
```

These are the password file lines posted by Robert (see the Solaris 10
revision of this tutorial), combined into one file.  Two lines came from
Solaris 10 systems (and they've been through "unshadow" run on both
passwd and shadow files), the third line came from an Ubuntu system (a
shadow file line only, which is slightly wrong as it relates to JtR's
use of it).

Let's start by extracting a clean John the Ripper 1.7.6 tarball (no
patches) and compiling John:

```
[solar@...ora12 john]$ tar xvjf john-1.7.6.tar.bz2
john-1.7.6/
john-1.7.6/doc/
john-1.7.6/doc/EXAMPLES
[...]
john-1.7.6/src/x86-sse.h
john-1.7.6/src/DES_vec.pl
john-1.7.6/README
[solar@...ora12 john]$ cd john-1.7.6/src/
[solar@...ora12 src]$ make -j8 linux-x86-64
ln -sf x86-64.h arch.h
[...]
ln -s john ../run/unique
make[1]: Leaving directory `/home/solar/john/john-1.7.6/src'
```

We've successfully compiled John.  Now let's try to use it:

```
[solar@...ora12 src]$ cd ../run/
[solar@...ora12 run]$ ./john ../../pw-sha-rs904c
Loaded 3 password hashes with 3 different salts (generic crypt(3) [?/64])
guesses: 0  time: 0:00:00:15 79% (1)  c/s: 201  trying: testU - test52
password         (robert)
password         (test)
password         (test)
guesses: 3  time: 0:00:00:22 100% (2)  c/s: 200  trying: 12345 - missy
```

I pressed "any key" at 15 seconds to obtain the non-100% status line
above.  It could be seen that John was trying username-based passwords
first.  Also, it was probably trying passwords with "99999" in them,
because of the shadow file line containing that string in the field
which JtR expects to be the GECOS field, but this is not seen above
(I did not catch it with my keypress).  You really ought to use the
included unshadow program to have JtR try the right user-specific
candidate passwords.

Then John proceeded with "pass 2", which is the wordlist mode, and it
tried "password" soon because it's found near the beginning of the
common passwords list in password.lst.

Now let's display the results properly:

```
[solar@...ora12 run]$ ./john --show ../../pw-sha-rs904c 
test:password:102:14::/home/test:/bin/sh
test:password:102:14::/home/test:/bin/sh
robert:password:14527:0:99999:7:::

3 password hashes cracked, 0 left
```

That's it.  But we were only using one out of four CPU cores, and we
were not using the Core i7 CPU's capability to simultaneously run two
threads or processes per core.  Let's try to use all eight logical CPUs
that the Linux kernel sees.  We need to make an OpenMP-enabled build.
First, clean out the old build:

```
[solar@...ora12 run]$ cd ../src/
[solar@...ora12 src]$ make clean
```

Then enable OpenMP.  We need to uncomment one of the OMPFLAGS lines near
the beginning of Makefile:

```
[solar@...ora12 src]$ vi Makefile
```

We locate the line for gcc and remove the leading "#" character.
Before our edits:

```
# gcc with OpenMP
#OMPFLAGS = -fopenmp
```

After the edits:

```
# gcc with OpenMP
OMPFLAGS = -fopenmp
```

(the true comment remains with its "#" character, but the variable
assignment is now uncommented).

Now let's make the new build:

```
[solar@...ora12 src]$ make -j8 linux-x86-64
ln -sf x86-64.h arch.h
[...]
gcc -c -Wall -O2 -fomit-frame-pointer -fopenmp -DHAVE_CRYPT -funroll-loops c3_fmt.c
[...]
ln -s john ../run/unique
make[1]: Leaving directory `/home/solar/john/john-1.7.6/src'
```

And let's test it:

```
[solar@...ora12 src]$ cd ../run/
[solar@...ora12 run]$ rm john.pot 
[solar@...ora12 run]$ ./john ../../pw-sha-rs904c 
Loaded 3 password hashes with 3 different salts (generic crypt(3) [?/64])
guesses: 0  time: 0:00:00:01 18% (1)  c/s: 564  trying: Robert99999g - Robert/
password         (robert)
password         (test)
password         (test)
guesses: 3  time: 0:00:00:06 100% (2)  c/s: 746  trying: 12345 - missy
```

This has completed in 6 seconds instead of 22.  With more precise timing
(used by John internally) the speedup was "only" 3.7x in this case (200 c/s
to 746 c/s).  The system appeared to be under some light load unrelated
to John, though.  Another test run was slightly faster:

```
guesses: 3  time: 0:00:00:05 100% (2)  c/s: 778  trying: 12345 - missy
```

This is a 3.9x speedup from parallelization, assuming that the 200 c/s
single process run could use all CPU time it wanted to.

Some speedup might be possible with "OMP_WAIT_POLICY=PASSIVE":

```
[solar@...ora12 run]$ OMP_WAIT_POLICY=PASSIVE ./john ../../pw-sha-rs904c
Loaded 3 password hashes with 3 different salts (generic crypt(3) [?/64])
guesses: 0  time: 0:00:00:02 51% (1)  c/s: 796  trying: Drr99999 - rbert99999
password         (robert)
password         (test)
password         (test)
guesses: 3  time: 0:00:00:05 100% (2)  c/s: 785  trying: 12345 - missy
```

The effect of this setting on overall JtR performance is
system-specific.  On another CPU (such as without SMT), gcc's default of
ACTIVE might be faster.

The "--show" option works as usual:

```
[solar@...ora12 run]$ ./john --show ../../pw-sha-rs904c 
test:password:102:14::/home/test:/bin/sh
test:password:102:14::/home/test:/bin/sh
robert:password:14527:0:99999:7:::

3 password hashes cracked, 0 left
```

Finally, here's how "unshadow" may be used.  As root, make the shadow
file temporarily available to our non-root account, assuming that the
home directories for "root" and "solar" are on the same filesystem:

```
[root@...ora12 ~]# pwd
/root
[root@...ora12 ~]# umask 077
[root@...ora12 ~]# cp /etc/shadow .
[root@...ora12 ~]# chown solar: shadow
[root@...ora12 ~]# ln shadow ~solar/
[root@...ora12 ~]# rm shadow
rm: remove regular file `shadow'? y
```

The "rm shadow" command removed just one of two hard-links to the shadow
file copy.

Under the non-root account, process the system's /etc/passwd file along
with the shadow file with "unshadow":

```
[solar@...ora12 run]$ umask 077
[solar@...ora12 run]$ chmod 600 ~/shadow
[solar@...ora12 run]$ ./unshadow /etc/passwd ~/shadow > pw-local
[solar@...ora12 run]$ shred -u ~/shadow
```

This assumes that no changes were made to /etc/passwd since we grabbed a
copy of /etc/shadow and until we ran the unshadow command.  "chmod 600"
is needed because /etc/shadow is mode 0 on Fedora 12 (at least on this
specific install), which gets inherited in the copy.  So we need to make
the file readable to "unshadow" and writable to "shred".  "umask 077" is
needed to ensure that our newly-created files are not readable to other
users (the default umask may be much more relaxed).

Now let's run John as usual:

```
[solar@...ora12 run]$ ./john pw-local
Loaded 2 password hashes with 2 different salts (generic crypt(3) [?/64])
guesses: 0  time: 0:00:00:05 0% (2)  c/s: 784  trying: kim - olivier
guesses: 0  time: 0:00:00:14 4% (2)  c/s: 812  trying: Canela - Dammit
guesses: 0  time: 0:00:00:20 6% (2)  c/s: 817  trying: scruffies - xcountries
guesses: 0  time: 0:00:02:17 37% (2)  c/s: 824  trying: sydney? - minnie?
guesses: 0  time: 0:00:02:26 41% (2)  c/s: 824  trying: nsbt - rbrts
Session aborted
```

or maybe:

```
[solar@...ora12 run]$ OMP_WAIT_POLICY=PASSIVE ./john pw-local
Loaded 2 password hashes with 2 different salts (generic crypt(3) [?/64])
guesses: 0  time: 0:00:00:09 3% (2)  c/s: 808  trying: nicholas - Buster
guesses: 0  time: 0:00:04:25 76% (2)  c/s: 828  trying: Foster0 - Logical0
guesses: 0  time: 0:00:04:42 80% (2)  c/s: 828  trying: 7rancid - 9michelle
Session aborted
```

My passwords are not getting cracked this easily.  Also, we're getting
slightly better performance with longer runs (these hashes use the same
iteration counts as Robert's, so a direct comparison is valid this
time) ... and the effect of "OMP_WAIT_POLICY=PASSIVE" is not obvious.

I was pressing Ctrl-C to interrupt these sessions.  It is possible to
continue an interrupted session in JtR's usual way:

```
[solar@...ora12 run]$ OMP_WAIT_POLICY=PASSIVE ./john --restore
Loaded 2 password hashes with 2 different salts (generic crypt(3) [?/64])
guesses: 0  time: 0:00:04:44 80% (2)  c/s: 827  trying: 9alexis - 9passwd
guesses: 0  time: 0:00:04:50 82% (2)  c/s: 827  trying: 9softball - 5fuckme
```

Alexander


Links
-------
*[John homepage](http://openwall.info/wiki/john)
*[John wiki](http://openwall.info/wiki/john)
Include any links to helpful example such as videos, webpages, etc.
