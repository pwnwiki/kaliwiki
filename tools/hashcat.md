# Tool Name

Notes
-------
Hashcat is the self-proclaimed world’s fastest CPU-based password recovery tool. 

Help Text
-------
```
hashcat, advanced password recovery

Usage: hashcat [options] hashfile [mask|wordfiles|directories]

=======
Options
=======

* General:

  -m,  --hash-type=NUM               Hash-type, see references below
  -a,  --attack-mode=NUM             Attack-mode, see references below
  -V,  --version                     Print version
  -h,  --help                        Print help
       --eula                        Print EULA
       --expire                      Print expiration date
       --quiet                       Suppress output

* Misc:

       --hex-salt                    Assume salt is given in hex
       --hex-charset                 Assume charset is given in hex

* Files:

  -o,  --outfile=FILE                Define outfile for recovered hash
       --outfile-format=NUM          Define outfile-format for recovered hash, see references below
  -p,  --separator=CHAR              Define separator char for hashlists/outfile
       --show                        Show cracked passwords only (see also --username)
       --left                        Show un-cracked passwords only (see also --username)
       --username                    Enable ignoring of usernames in hashfile (recommended: also use --show)
       --remove                      Enable remove of hash once it is cracked
       --stdout                      stdout mode
       --disable-potfile             do not write potfile
       --debug-file=FILE             debug-file
       --debug-mode=NUM              Defines the debug mode (hybrid only by using rules), see references below
  -e,  --salt-file=FILE              salts-file for unsalted hashlists

* Resources:

  -c,  --segment-size=NUM            Size in MB to cache from the wordfile
  -n,  --threads=NUM                 number of threads
  -s,  --words-skip=NUM              skip number of words (for resume)
  -l,  --words-limit=NUM             limit number of words (for distributed)

* Rules:

  -r,  --rules-file=FILE             Rules-file use: -r 1.rule
  -g,  --generate-rules=NUM          Generate NUM random rules
       --generate-rules-func-min=NUM Force NUM functions per random rule min
       --generate-rules-func-max=NUM Force NUM functions per random rule max
       --generate-rules-seed=NUM     Force RNG seed to NUM

* Custom charsets:

  -1,  --custom-charset1=CS          User-defined charsets
  -2,  --custom-charset2=CS          Example:
  -3,  --custom-charset3=CS          --custom-charset1=?dabcdef : sets charset ?1 to 0123456789abcdef
  -4,  --custom-charset4=CS          -2 mycharset.hcchr : sets charset ?2 to chars contained in file

* Toggle-Case attack-mode specific:

       --toggle-min=NUM              number of alphas in dictionary minimum
       --toggle-max=NUM              number of alphas in dictionary maximum

* Mask-attack attack-mode specific:

       --pw-min=NUM                  Password-length minimum
       --pw-max=NUM                  Password-length maximum

* Permutation attack-mode specific:

       --perm-min=NUM                Filter words shorter than NUM
       --perm-max=NUM                Filter words larger than NUM

* Table-Lookup attack-mode specific:

  -t,  --table-file=FILE             table file
       --table-min=NUM               number of chars in dictionary minimum
       --table-max=NUM               number of chars in dictionary maximum

==========
References
==========

* Outfile formats:

    1 = hash[:salt]
    2 = plain
    3 = hash[:salt]:plain
    4 = hex_plain
    5 = hash[:salt]:hex_plain
    6 = plain:hex_plain
    7 = hash[:salt]:plain:hex_plain
    8 = plain:position

* Debug mode output formats (for hybrid mode only, by using rules):

    1 = save finding rule
    2 = save original word
    3 = save original word and finding rule

* Built-in charsets:

   ?l = abcdefghijklmnopqrstuvwxyz
   ?u = ABCDEFGHIJKLMNOPQRSTUVWXYZ
   ?d = 0123456789
   ?s =  !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
   ?a = ?l?u?d?s

* Attack modes:

    0 = Straight
    1 = Combination
    2 = Toggle-Case
    3 = Brute-force
    4 = Permutation
    5 = Table-Lookup

* Hash types:

    0 = MD5
   10 = md5($pass.$salt)
   20 = md5($salt.$pass)
   30 = md5(unicode($pass).$salt)
   40 = md5($salt.unicode($pass))
   50 = HMAC-MD5 (key = $pass)
   60 = HMAC-MD5 (key = $salt)
  100 = SHA1
  110 = sha1($pass.$salt)
  120 = sha1($salt.$pass)
  130 = sha1(unicode($pass).$salt)
  140 = sha1($salt.unicode($pass))
  150 = HMAC-SHA1 (key = $pass)
  160 = HMAC-SHA1 (key = $salt)
  200 = MySQL
  300 = MySQL4.1/MySQL5
  400 = phpass, MD5(Wordpress), MD5(phpBB3)
  500 = md5crypt, MD5(Unix), FreeBSD MD5, Cisco-IOS MD5
  800 = SHA-1(Django)
  900 = MD4
 1000 = NTLM
 1100 = Domain Cached Credentials, mscash
 1400 = SHA256
 1410 = sha256($pass.$salt)
 1420 = sha256($salt.$pass)
 1430 = sha256(unicode($pass).$salt)
 1440 = sha256($salt.unicode($pass))
 1450 = HMAC-SHA256 (key = $pass)
 1460 = HMAC-SHA256 (key = $salt)
 1600 = md5apr1, MD5(APR), Apache MD5
 1700 = SHA512
 1710 = sha512($pass.$salt)
 1720 = sha512($salt.$pass)
 1730 = sha512(unicode($pass).$salt)
 1740 = sha512($salt.unicode($pass))
 1750 = HMAC-SHA512 (key = $pass)
 1760 = HMAC-SHA512 (key = $salt)
 1800 = SHA-512(Unix)
 2400 = Cisco-PIX MD5
 2500 = WPA/WPA2
 2600 = Double MD5
 3200 = bcrypt, Blowfish(OpenBSD)
 3300 = MD5(Sun)
 3500 = md5(md5(md5($pass)))
 3610 = md5(md5($salt).$pass)
 3710 = md5($salt.md5($pass))
 3720 = md5($pass.md5($salt))
 3810 = md5($salt.$pass.$salt)
 3910 = md5(md5($pass).md5($salt))
 4010 = md5($salt.md5($salt.$pass))
 4110 = md5($salt.md5($pass.$salt))
 4210 = md5($username.0.$pass)
 4300 = md5(strtoupper(md5($pass)))
 4400 = md5(sha1($pass))
 4500 = sha1(sha1($pass))
 4600 = sha1(sha1(sha1($pass)))
 4700 = sha1(md5($pass))
 4800 = MD5(Chap)
 5000 = SHA-3(Keccak)
 5100 = Half MD5
 5200 = Password Safe SHA-256
 5300 = IKE-PSK MD5
 5400 = IKE-PSK SHA1
 5500 = NetNTLMv1-VANILLA / NetNTLMv1-ESS
 5600 = NetNTLMv2
 5700 = Cisco-IOS SHA256
 5800 = Samsung Android Password/PIN
 6300 = AIX {smd5}
 6400 = AIX {ssha256}
 6500 = AIX {ssha512}
 6700 = AIX {ssha1}
 6900 = GOST, GOST R 34.11-94
 7000 = Fortigate (FortiOS)
 7100 = OS X v10.8
 7200 = GRUB 2
 7300 = IPMI2 RAKP HMAC-SHA1
 7400 = sha256crypt, SHA256(Unix)
 9999 = Plaintext

* Specific hash types:

   11 = Joomla
   21 = osCommerce, xt:Commerce
  101 = nsldap, SHA-1(Base64), Netscape LDAP SHA
  111 = nsldaps, SSHA-1(Base64), Netscape LDAP SSHA
  112 = Oracle 11g
  121 = SMF > v1.1
  122 = OS X v10.4, v10.5, v10.6
  123 = EPi
  131 = MSSQL(2000)
  132 = MSSQL(2005)
  141 = EPiServer 6.x < v4
 1441 = EPiServer 6.x > v4
 1711 = SSHA-512(Base64), LDAP {SSHA512}
 1722 = OS X v10.7
 1731 = MSSQL(2012)
 2611 = vBulletin < v3.8.5
 2711 = vBulletin > v3.8.5
 2811 = IPB2+, MyBB1.2+
 3721 = WebEdition CMS
 7600 = Redmine Project Management Web App

```

Example Usage
-------
There is a wiki [here](http://hashcat.net/wiki/doku.php?id=start)


Links
-------
1. [hashcat](http://hashcat.net/hashcat/)
1. [youtube](https://www.youtube.com/watch?v=fCNOIheD-Is)
1. [Cracking WPA and WPA2](http://www.blackmoreops.com/2014/03/27/cracking-wpa-wpa2-with-hashcat-kali-linux/#)
