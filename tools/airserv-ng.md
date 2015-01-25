AIRSERV-NG

NAME
       airserv-ng - a wireless card server

SYNOPSIS
       airserv-ng <options>

DESCRIPTION
       airserv-ng  is  a  wireless  card server which allows multiple wireless
       application programs to independently use a wireless card via a client-
       server  TCP  network connection. All operating system and wireless card
       driver specific code is incorporated into the server.  This  eliminates
       the  need for each wireless application to contain the complex wireless
       card and driver logic. It is also supports multiple operating systems.

OPTIONS
       -h     Shows the help screen.

       -p <port>
              TCP port to listen on (by default: 666).

       -d <iface>
              Wifi interface to use.

       -c <chan>
              Lock interface to this channel.

       -v <level>
              Debug level. There are 3 debug levels.  Debug level of  1  shows
              client  connection/disconnection  (default).   Debug  level of 2
              shows  channel  change  requests  and  invalid  client   command
              requests in addition to the debug level 1 messages.  Debug level
              of 3 displays a message each time a packet (and its  length)  is
              sent  to  the client. It also include messages from level 2 (and
              1).