# acccheck

Notes
-------
The tool is designed as a password dictionary attack tool that targets windows authentication via the SMB protocol. It is really a wrapper script around the ‘smbclient’ binary, and as a result is dependent on it for its execution.

Help Text
-------
```
acccheck.pl v0.2.1 - By Faiz

Description:
Attempts to connect to the IPC$ and ADMIN$ shares depending on which flags have been
chosen, and tries a combination of usernames and passwords in the hope to identify
the password to a given account via a dictionary password guessing attack.

Usage = ./acccheck.pl [optional]

 -t [single host IP address]
 OR 
 -T [file containing target ip address(es)]

Optional:
 -p [single password]
 -P [file containing passwords]
 -u [single user]
 -U [file containing usernames]
 -v [verbose mode]

Examples
Attempt the 'Administrator' account with a [BLANK] password.
	acccheck.pl -t 10.10.10.1
Attempt all passwords in 'password.txt' against the 'Administrator' account.
	acccheck.pl -t 10.10.10.1 -P password.txt
Attempt all password in 'password.txt' against all users in 'users.txt'.
	acccehck.pl -t 10.10.10.1 -U users.txt -P password.txt
Attempt a single password against a single user.
	acccheck.pl -t 10.10.10.1 -u administrator -p password

```

Example Usage
-------
The simplest way to run the tool is as follows:
```
./acccheck.pl -t 10.10.10.1
```
This mode of execution attempts to connect to the target ADMIN$ share with the username ‘Administrator’ and a [BLANK] for the password.
```
`./acccheck.pl -t 10.10.10.1 -u test -p test
```
This mode of execution attempts to connect to the target IPC$ share with the username `test` and a password `test`.

Each `-t`, `-u` and `-p` flags can be substituted by `-T`, `-U` and `-P`, where each represents an input file rather than a single input from standard in.

E.g.
```
./acccheck.pl -T iplist -U userfile -P passwordfile
```
Only use `-v` mode on very small dictionaries, otherwise, this has the affect of slowing the scan down to the rate the system writes to standard out.

Any username/password combinations found are written to a file called ‘cracked’ in the working directory.

Links
-------
Notes and example usage from: https://labs.portcullis.co.uk/tools/acccheck/

