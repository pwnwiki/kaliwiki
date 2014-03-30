# sslsniff

Notes
-------

Help Text
-------
```
Usage: sslsniff [options]

Modes:
-a	Authority mode.  Specify a certificate that will act as a CA.
-t	Targeted mode.  Specify a directory full of certificates to target.

Required Options:
-c <file|directory>	File containing CA cert/key (authority mode) or 
			directory containing a collection of certs/keys
			(targeted mode)
-s <port>		Port to listen on for SSL interception.
-w <file>		File to log to

Optional Options:
-u <updateLocation>	Loction of any Firefox XML update files.
-m <certificateChain>	Location of any intermediary certificates.
-h <port>		Port to listen on for HTTP interception (required for
			fingerprinting).
-f <ff,ie,safari,opera,ios>	Only intercept requests from the specified browser(s).
-d			Deny OCSP requests for our certificates.
-p			Only log HTTP POSTs
-e <url>		Intercept Mozilla Addon Updates
-j <sha256>		The sha256sum value of the addon to inject

```

Example Usage
-------

Links
-------

