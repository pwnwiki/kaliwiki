# thc-ssl-dos

Notes
-------
THC-SSL-DOS is a tool to verify the performance of SSL.

Establishing a secure SSL connection requires 15x more processing
power on the server than on the client.

THC-SSL-DOS exploits this asymmetric property by overloading the
server and knocking it off the Internet.

This problem affects all SSL implementations today. The vendors are aware
of this problem since 2003 and the topic has been widely discussed.

This attack further exploits the SSL secure Renegotiation feature
to trigger thousands of renegotiations via single TCP connection.


Help Text
-------
```
     ______________ ___  _________
     \__    ___/   |   \ \_   ___ \
       |    | /    ~    \/    \  \/
       |    | \    Y    /\     \____
       |____|  \___|_  /  \______  /
                     \/          \/
            http://www.thc.org

          Twitter @hackerschoice

Greetingz: the french underground

./thc-ssl-dos [options] <ip> <port>
  -h      help
  -l <n>  Limit parallel connections [default: 400]



```

Example Usage
-------

```

```

Links
-------
[The Hackers Choioce](https://www.thc.org/thc-ssl-dos/)



