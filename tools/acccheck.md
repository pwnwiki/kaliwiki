# acccheck

Notes
-------

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

Links
-------

