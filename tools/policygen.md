# policygen

Notes
-------
PolicyGen - Analyze and Generate password masks according to a password policy
This tool is part of PACK (Password Analysis and Cracking Kit)


Copyright (C) 2013 Peter Kacherginsky


Help Text
-------
```
Usage: policygen [options]

Type --help for more options

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  --length=8            Password length
  -o masks.txt, --output=masks.txt
                        Save masks to a file
  --pps=1000000000      Passwords per Second
  -v, --verbose         

  Password Policy:
    Define the minimum (or maximum) password strength policy that you
    would like to test

    --mindigits=1       Minimum number of digits
    --minlower=1        Minimum number of lower-case characters
    --minupper=1        Minimum number of upper-case characters
    --minspecial=1      Minimum number of special characters
    --maxdigits=3       Maximum number of digits
    --maxlower=3        Maximum number of lower-case characters
    --maxupper=3        Maximum number of upper-case characters
    --maxspecial=3      Maximum number of special characters

```

Example Usage
-------
From PACK's github:

```
PolicyGen
=========

A lot of the mask and dictionary attacks will fail in the corporate environment with minimum password complexity requirements. Instead of resorting to a pure bruteforcing attack, we can leverage known or guessed password complexity rules to avoid trying password candidates that are not compliant with the policy or inversely only audit for noncompliant passwords. Using PolicyGen, you will be able to generate a collection of masks following the password complexity in order to significantly reduce the cracking time. 

Below is a sample session where we generate all valid password masks for an environment requiring at least one digit, one upper, and one special characters.

    $ python policygen.py --minlength 8 --maxlength 8 --minlower 1 --minupper 1 --mindigit 1 --minspecial 1 -o complexity.hcmask
                           _ 
         PolicyGen #.#.#  | |
          _ __   __ _  ___| | _
         | '_ \ / _` |/ __| |/ /
         | |_) | (_| | (__|   < 
         | .__/ \__,_|\___|_|\_\
         | |                    
         |_| iphelix@thesprawl.org


    [*] Saving generated masks to [complexity.hcmask]
    [*] Using 1,000,000,000 keys/sec for calculations.
    [*] Password policy:
        Pass Lengths: min:8 max:8
        Min strength: l:1 u:1 d:1 s:1
        Max strength: l:None u:None d:None s:None
    [*] Generating [compliant] masks.
    [*] Generating 8 character password masks.
    [*] Total Masks:  65536 Time: 76 days, 18:50:04
    [*] Policy Masks: 40824 Time: 35 days, 0:33:09

From the above output you can see that we have generated 40824 masks matching the specified complexity that will take about 35 days to run at the speed of 1,000,000,000 keys/sec.

In case you are simply performing a password audit and tasked to discover only non-compliant passwords you can specify '--noncompliant' flag to invert generated masks:

    $ python policygen.py --minlength 8 --maxlength 8 --minlower 1 --minupper 1 --mindigit 1 --minspecial 1 -o noncompliant.hcmask -q --noncompliant
    [*] Saving generated masks to [noncompliant.hcmask]
    [*] Using 1,000,000,000 keys/sec for calculations.
    [*] Password policy:
        Pass Lengths: min:8 max:8
        Min strength: l:1 u:1 d:1 s:1
        Max strength: l:None u:None d:None s:None
    [*] Generating [non-compliant] masks.
    [*] Generating 8 character password masks.
    [*] Total Masks:  65536 Time: 76 days, 18:50:04
    [*] Policy Masks: 24712 Time: 41 days, 18:16:55

Let's see some of the non-compliant masks generated above using the '--showmasks' flag:

    $ python policygen.py --minlength 8 --maxlength 8 --minlower 1 --minupper 1 --mindigit 1 --minspecial 1 -o noncompliant.hcmask -q --noncompliant --showmasks
    [*] Saving generated masks to [noncompliant.hcmask]
    [*] Using 1,000,000,000 keys/sec for calculations.
    [*] Password policy:
        Pass Lengths: min:8 max:8
        Min strength: l:1 u:1 d:1 s:1
        Max strength: l:None u:None d:None s:None
    [*] Generating [non-compliant] masks.
    [*] Generating 8 character password masks.
    [ 8] ?d?d?d?d?d?d?d?d               [l: 0 u: 0 d: 8 s: 0] [ 0:00:00]  
    [ 8] ?d?d?d?d?d?d?d?l               [l: 1 u: 0 d: 7 s: 0] [ 0:00:00]  
    [ 8] ?d?d?d?d?d?d?d?u               [l: 0 u: 1 d: 7 s: 0] [ 0:00:00]  
    [ 8] ?d?d?d?d?d?d?d?s               [l: 0 u: 0 d: 7 s: 1] [ 0:00:00]  
    ... 
    [ 8] ?s?s?s?s?s?s?s?d               [l: 0 u: 0 d: 1 s: 7] [ 0:07:06]  
    [ 8] ?s?s?s?s?s?s?s?l               [l: 1 u: 0 d: 0 s: 7] [ 0:18:28]  
    [ 8] ?s?s?s?s?s?s?s?u               [l: 0 u: 1 d: 0 s: 7] [ 0:18:28]  
    [ 8] ?s?s?s?s?s?s?s?s               [l: 0 u: 0 d: 0 s: 8] [ 0:23:26]  
    [*] Total Masks:  65536 Time: 76 days, 18:50:04
    [*] Policy Masks: 24712 Time: 41 days, 18:16:55

As you can see all of the masks have at least one missing password complexity requirement. Interestingly with fewer generated masks it takes longer to attack because of long running masks like '?s?s?s?s?s?s?s?s'.

Specifying maximum complexity
-----------------------------

It is also possible to specify maximum password complexity using --maxlower, --maxupper, --maxdigit and --maxspecial flags in order to fine-tune you attack. For example, below is a sample site which enforces password policy but does not allow any special characters:

    $ python policygen.py --minlength 8 --maxlength 8 --minlower 1 --minupper 1 --mindigit 1 --maxspecial 0 -o maxcomplexity.hcmask -q
    [*] Saving generated masks to [maxcomplexity.hcmask]
    [*] Using 1,000,000,000 keys/sec for calculations.
    [*] Password policy:
        Pass Lengths: min:8 max:8
        Min strength: l:1 u:1 d:1 s:None
        Max strength: l:None u:None d:None s:0
    [*] Generating [compliant] masks.
    [*] Generating 8 character password masks.
    [*] Total Masks:  65536 Time: 76 days, 18:50:04
    [*] Policy Masks: 5796 Time: 1 day, 20:20:55

```

Links
-------
* [github](https://github.com/iphelix/pack/blob/master/policygen.py)
