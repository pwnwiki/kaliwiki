# THC-pptp-bruter

Notes
-------
Brute force program against pptp vpn endpoints (tcp port 1723). Fully standalone. Supports latest MSChapV2 authentication. Tested against Windows and Cisco gateways. 
Exploits a weakness in Microsoft's anti-brute force implementation which makes it possible to try 300 passwords the second.


Help Text
-------
```
thc-pptp-bruter [options] <remote host IP>
  -v        Verbose output / Debug output
  -W        Disable windows hack [default: enabled]
  -u <user> User [default: administrator]
  -w <file> Wordlist file [default: stdin]
  -p <n>    PPTP port [default: 1723]
  -n <n>    Number of parallel tries [default: 5]
  -l <n>    Limit to n passwords / sec [default: 100]

Windows-Hack reuses the LCP connection with the same caller-id. This
gets around MS's anti-brute forcing protection. It's enabled by default.


```

Example Usage
-------


```

```

Links
-------
