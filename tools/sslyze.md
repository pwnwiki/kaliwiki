# sslyze

Notes
-------

Help Text
-------
```


 REGISTERING AVAILABLE PLUGINS
 -----------------------------

  PluginCompression
  PluginOpenSSLCipherSuites
  PluginSessionResumption
  PluginCertInfo
  PluginSessionRenegotiation



Usage: sslyze [options] target1.com target2.com:443 etc...

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  --xml_out=XML_FILE    Writes the scan results as an XML document to the file
                        XML_FILE.
  --targets_in=TARGETS_IN
                        Reads the list of targets to scan from the file
                        TARGETS_IN. It should contain one host:port per line.
  --timeout=TIMEOUT     Sets the timeout value in seconds used for every
                        socket connection made to the target server(s).
                        Default is 5s.
  --https_tunnel=HTTPS_TUNNEL
                        Sets an HTTP CONNECT proxy to tunnel SSL traffic to
                        the target server(s). HTTP_TUNNEL should be
                        'host:port'. Requires Python 2.7
  --starttls=STARTTLS   Identifies the target server(s) as a SMTP or an XMPP
                        server(s) and scans the server(s) using STARTTLS.
                        STARTTLS should be 'smtp' or 'xmpp'.
  --xmpp_to=XMPP_TO     Optional setting for STARTTLS XMPP.  XMPP_TO should be
                        the hostname to be put in the 'to' attribute of the
                        XMPP stream. Default is the server's hostname.
  --regular             Regular HTTPS scan; shortcut for --sslv2 --sslv3
                        --tlsv1 --reneg --resum --certinfo --http_get
                        --hide_rejected_ciphers --compression --tlsv1_1
                        --tlsv1_2

  Client certificate support:
    --cert=CERT         Client certificate filename.
    --certform=CERTFORM
                        Client certificate format. DER or PEM (default).
    --key=KEY           Client private key filename.
    --keyform=KEYFORM   Client private key format. DER or PEM (default).
    --pass=KEYPASS      Client private key passphrase.

  PluginCompression:
    --compression       Tests the server for Zlib compression support.

  PluginOpenSSLCipherSuites:
    Scans the target server for supported OpenSSL cipher suites.

    --sslv2             Lists the SSL 2.0 OpenSSL cipher suites supported by
                        the server.
    --sslv3             Lists the SSL 3.0 OpenSSL cipher suites supported by
                        the server.
    --tlsv1             Lists the TLS 1.0 OpenSSL cipher suites supported by
                        the server.
    --tlsv1_1           Lists the TLS 1.1 OpenSSL cipher suites supported by
                        the server.
    --tlsv1_2           Lists the TLS 1.2 OpenSSL cipher suites supported by
                        the server.
    --http_get          Option - For each cipher suite, sends an HTTP GET
                        request after completing the SSL handshake and returns
                        the HTTP status code.
    --hide_rejected_ciphers
                        Option - Hides the (usually long) list of cipher
                        suites that were rejected by the server.

  PluginSessionResumption:
    Analyzes the target server's SSL session resumption capabilities.

    --resum             Tests the server for session ressumption support,
                        using session IDs and TLS session tickets (RFC 5077).
    --resum_rate        Performs 100 session resumptions with the target
                        server, in order to estimate the session resumption
                        rate.

  PluginCertInfo:
    --certinfo=CERTINFO
                        Verifies the target server's certificate validity
                        against Mozilla's trusted root store, and prints
                        relevant fields of the certificate. CERTINFO should be
                        'basic' or 'full'.

  PluginSessionRenegotiation:
    --reneg             Tests the target server's support for client-initiated
                        renegotiations and secure renegotiations.

```

Example Usage
-------

Links
-------

