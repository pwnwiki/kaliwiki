# ettercap -h

ettercap NG-0.7.4.2 copyright 2001-2005 ALoR & NaGA


Usage: ettercap [OPTIONS] [TARGET1] [TARGET2]

TARGET is in the format MAC/IPs/PORTs (see the man for further detail)

Sniffing and Attack options:
  -M, --mitm <METHOD:ARGS>    perform a mitm attack
  -o, --only-mitm             don't sniff, only perform the mitm attack
  -B, --bridge <IFACE>        use bridged sniff (needs 2 ifaces)
  -p, --nopromisc             do not put the iface in promisc mode
  -u, --unoffensive           do not forward packets
  -r, --read <file>           read data from pcapfile <file>
  -f, --pcapfilter <string>   set the pcap filter <string>
  -R, --reversed              use reversed TARGET matching
  -t, --proto <proto>         sniff only this proto (default is all)

User Interface Type:
  -T, --text                  use text only UI
       -q, --quiet                 do not display packet contents
       -s, --script <CMD>          issue these commands to the GUI
  -C, --curses                use curses UI
  -G, --gtk                   use GTK+ GUI
  -D, --daemon                daemonize ettercap (no UI)

Logging options:
  -w, --write <file>          write sniffed data to pcapfile <file>
  -L, --log <logfile>         log all the traffic to this <logfile>
  -l, --log-info <logfile>    log only passive infos to this <logfile>
  -m, --log-msg <logfile>     log all the messages to this <logfile>
  -c, --compress              use gzip compression on log files

Visualization options:
  -d, --dns                   resolves ip addresses into hostnames
  -V, --visual <format>       set the visualization format
  -e, --regex <regex>         visualize only packets matching this regex
  -E, --ext-headers           print extended header for every pck
  -Q, --superquiet            do not display user and password

General options:
  -i, --iface <iface>         use this network interface
  -I, --iflist                show all the network interfaces
  -n, --netmask <netmask>     force this <netmask> on iface
  -A, --address <address>     force this local <address> on iface
  -P, --plugin <plugin>       launch this <plugin>
  -F, --filter <file>         load the filter <file> (content filter)
  -z, --silent                do not perform the initial ARP scan
  -j, --load-hosts <file>     load the hosts list from <file>
  -k, --save-hosts <file>     save the hosts list to <file>
  -W, --wep-key <wkey>        use this wep key to decrypt wifi packets
  -a, --config <config>       use the alterative config file <config>

Standard options:
  -v, --version               prints the version and exit
  -h, --help                  this help screen

