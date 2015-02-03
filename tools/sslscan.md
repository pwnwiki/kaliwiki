# sslscan

Notes
-------

Help Text
-------
```
                   _
           ___ ___| |___  ___ __ _ _ __
          / __/ __| / __|/ __/ _` | '_ \
          \__ \__ \ \__ \ (_| (_| | | | |
          |___/___/_|___/\___\__,_|_| |_|

                  Version 1.8.2
             http://www.titania.co.uk
        Copyright Ian Ventura-Whiting 2009

SSLScan is a fast SSL port scanner. SSLScan connects to SSL
ports and determines what  ciphers are supported, which are
the servers  preferred  ciphers,  which  SSL  protocols  are
supported  and   returns  the   SSL   certificate.   Client
certificates /  private key can be configured and output is
to text / XML.

Command:
  sslscan [Options] [host:port | host]

Options:
  --targets=<file>     A file containing a list of hosts to
                       check.  Hosts can  be supplied  with
                       ports (i.e. host:port).
  --no-failed          List only accepted ciphers  (default
                       is to listing all ciphers).
  --ssl2               Only check SSLv2 ciphers.
  --ssl3               Only check SSLv3 ciphers.
  --tls1               Only check TLSv1 ciphers.
  --pk=<file>          A file containing the private key or
                       a PKCS#12  file containing a private
                       key/certificate pair (as produced by
                       MSIE and Netscape).
  --pkpass=<password>  The password for the private  key or
                       PKCS#12 file.
  --certs=<file>       A file containing PEM/ASN1 formatted
                       client certificates.
  --starttls           If a STARTTLS is required to kick an
                       SMTP service into action.
  --http               Test a HTTP connection.
  --bugs               Enable SSL implementation  bug work-
                       arounds.
  --xml=<file>         Output results to an XML file.
  --version            Display the program version.
  --help               Display the  help text  you are  now
                       reading.
Example:
  sslscan 127.0.0.1

```

Example Usage
-------

Links
-------

