# autopsy

Notes
-------
Autopsy® is a digital forensics platform and graphical interface to The Sleuth Kit® and other digital forensics tools.

Help Text
-------
```
usage: /usr/bin/autopsy [-c] [-C] [-d evid_locker] [-i device filesystem mnt] [-p port] [remoteaddr]
  -c: force a cookie in the URL
  -C: force NO cookie in the URL
  -d dir: specify the evidence locker directory
  -i device filesystem mnt: Specify info for live analysis
  -p port: specify the server port (default: 9999)
  remoteaddr: specify the host with the browser (default: localhost)
```

Example Usage
-------
```
root@kali:~/kaliwiki/tools# autopsy 

============================================================================

                       Autopsy Forensic Browser 
                  http://www.sleuthkit.org/autopsy/
                             ver 2.24 

============================================================================
Evidence Locker: /var/lib/autopsy
Start Time: Tue Apr 22 15:06:35 2014
Remote Host: localhost
Local Port: 9999

Open an HTML browser on the remote host and paste this URL in it:

    http://localhost:9999/autopsy

Keep this process running and use <ctrl-c> to exit
```

Links
-------
[1] http://www.sleuthkit.org/autopsy/
[2] http://wiki.sleuthkit.org/index.php?title=Autopsy_User%27s_Guide