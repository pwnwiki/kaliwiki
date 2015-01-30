# sslh

Notes
-------
sslh - Applicative protocol multiplexer, accepts connections on specified ports, and forwards them further based on tests performed on the first data packet sent by the remote client.

Help Text
-------
```
sslh: option '--http' requires an argument
sslh v1.13b
usage:
	sslh  [-v] [-i] [-V] [-f] [-n] [-F <file>]
	[-t <timeout>] [-P <pidfile>] -u <username> -p <add> [-p <addr> ...] 


-v: verbose
-V: version
-f: foreground
-n: numeric output
-F: use configuration file
-t: timeout before connecting to SSH.
-p: address and port to listen on.
    Can be used several times to bind to several addresses.
--[ssh,ssl,...]: where to connect connections from corresponding protocol.
-F: specify a configuration file
-P: PID file.
-i: Run as a inetd service.
```

Example Usage
-------

Links
-------
[Official site](http://www.rutschle.net/tech/sslh.shtml)

[sslh Github project](https://github.com/yrutschle/sslh)

