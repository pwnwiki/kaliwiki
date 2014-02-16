# netmask

Notes
-------

Help Text
-------
```
This is netmask, an address netmask generation utility
Usage: netmask spec [spec ...]
  -h, --help			Print a summary of the options
  -v, --version			Print the version number
  -d, --debug			Print status/progress information
  -s, --standard		Output address/netmask pairs
  -c, --cidr			Output CIDR format address lists
  -i, --cisco			Output Cisco style address lists
  -r, --range			Output ip address ranges
  -x, --hex			Output address/netmask pairs in hex
  -o, --octal			Output address/netmask pairs in octal
  -b, --binary			Output address/netmask pairs in binary
  -n, --nodns			Disable DNS lookups for addresses
Definitions:
  a spec can be any of:
    address
    address:address
    address:+address
    address/mask
  an address can be any of:
    N		decimal number
    0N		octal number
    0xN		hex number
    N.N.N.N	dotted quad
    hostname	dns domain name
  a mask is the number of bits set to one from the left
```

Example Usage
-------

Links
-------
