# dictstat

Notes
-------

"The dictstat Python script is a great little tool for password cracking results analysis or for regular wordlist analysis." [1]


Help Text
-------
```
Usage: dictstat [options] passwords.txt

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -l 8, --length=8      Password length filter.
  -c loweralpha, --charset=loweralpha
                        Password charset filter.
  -m stringdigit, --mask=stringdigit
                        Password mask filter
  -o masks.csv, --maskoutput=masks.csv
                        Save masks to a file
```

Example Usage
-------
"dictstat Password Cracking Results And Wordlist Analysis: Basic Usage" [1]

```
root@bt:/pentest/passwords/pack# ./dictstat.py /root/wordlists/500-worst-passwords.txt
[*] Using Psyco to accelerate parsing.
[*] Analyzing passwords: /root/wordlists/500-worst-passwords.txt
[+] Analyzing 100% (500/500) passwords
    NOTE: Statistics below is relative to the number of analyzed passwords, not total number of passwords
 
[*] Line Count Statistics...
[+]                         6: 46% (233)
[+]                         7: 19% (96)
[+]                         5: 13% (65)
[+]                         4: 11% (59)
[+]                         8: 09% (45)
 
[*] Mask statistics...
[+]                 allstring: 90% (454)
[+]                  alldigit: 07% (37)
[+]               stringdigit: 01% (9)
 
[*] Charset statistics...
[+]                loweralpha: 90% (454)
[+]                   numeric: 07% (37)
[+]             loweralphanum: 01% (9)
 
[*] Advanced Mask statistics...
[+]              ?l?l?l?l?l?l: 43% (219)
[+]            ?l?l?l?l?l?l?l: 18% (90)
[+]                ?l?l?l?l?l: 12% (62)
[+]                  ?l?l?l?l: 08% (43)
[+]          ?l?l?l?l?l?l?l?l: 08% (40)
[+]                  ?d?d?d?d: 03% (16)
[+]              ?d?d?d?d?d?d: 02% (12)
root@bt:/pentest/passwords/pack#
```
"The output above provides us all sorts of information about the 500 word passwords wordlist including the breakdown of password length, password mask statistics, password charset statistics, and the actual password masks that can be used to crack like passwords. You can see that the majority or 46% of the passwords are six characters long, the longest passwords are eight characters long, and the shortest passwords analyzed are four characters in length. Note that there are also 2 password lengths not listed in the output and each of those passwords are a single character in length as dictstat displays the top results and may not display every single length result. Also the vast majority of the combinations are all lowercase characters (total of 454 out of 500) with the last 46 passwords either being all digits or lowercase + digits. Notice that in this password list there are no passwords with special characters as this is the five hundred worst passwords and special characters would make the passwords more complex and harder to crack thus excluding them from this list. Last but not least we see the password masks that could be used with tools such as oclHashcat to provide a higher probability of cracking future password hashes from the same location these passwords were obtained from."[1]

Links
-------
1. [question-defense](http://www.question-defense.com/2012/12/16/dictstat-backtrack-5-privilege-escalation-password-attacks-offline-attacks-dictstat)