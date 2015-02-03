# lsadump

Notes
-------
This is an application to dump the contents of the LSA secrets on a machine, provided you are an Administrator. It uses the same technique as pwdump2 to bypass restrictions that Microsoft added to LsaRetrievePrivateData(), which cause the original lsadump to fail.


Help Text
-------
```
usage: /usr/bin/lsadump <system hive> <security hive>
```

Example Usage
-------
Post-Exploitation in Windows: From Local Admin To Domain Admin (efficiently)

Quick: Dump LSA Secrets (lsadump)
If any Windows services are running under a domain account, then the passwords for those accounts must be stored locally in a reversible format.  LSAdump2, LSASecretsDump, pwdumpx, gsecdump or Cain & Abel can recover these.
You might have to stare at the output of lsadump and the list of services in
After you’ve correlated plain text passwords from the “_SC_<service name>” sections of LSAdump with the domain usernames from services.msc using the short “service name”, you should a list of domain accounts and cleartext passwords.
Investigate your new found accounts and see if you’re domain admin yet.
(stolen from pentest monkey)


Links
-------
[Volatility](https://code.google.com/p/volatility/source/browse/branches/Volatility-2.0.1/volatility/plugins/registry/lsadump.py)
[Pentest Monkey](http://pentestmonkey.net/uncategorized/from-local-admin-to-domain-admin)
[Video](https://www.youtube.com/watch?v=7qQwVrCFE60) showing use with volatility
