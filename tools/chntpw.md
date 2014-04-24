# chntpw

Notes
-------
This  manual page documents briefly the chntpw command. This manual page was written for the Debian distribution because the original program does not have a manual page.

chntpw is a utility to view some information and change user passwords in a Windows NT/2000 SAM userdatabase file, usually located at \WINDOWS\system32\config\SAM on the Windows file system. It is not necessary to
know the old passwords to reset them. In addition it contains a simple registry editor (same size data writes) and hex-editor with which the information contained in a registry file can be browsed and modified.

Help Text
-------
```
chntpw version 0.99.6 080526 (sixtyfour), (c) Petter N Hagen
chntpw: change password of a user in a NT/2k/XP/2k3/Vista SAM file, or invoke registry editor.
chntpw [OPTIONS] <samfile> [systemfile] [securityfile] [otherreghive] [...]
 -h          This message
 -u <user>   Username to change, Administrator is default
 -l          list all users in SAM file
 -i          Interactive. List users (as -l) then ask for username to change
 -e          Registry editor. Now with full write support!
 -d          Enter buffer debugger instead (hex editor), 
 -t          Trace. Show hexdump of structs/segments. (deprecated debug function)
 -v          Be a little more verbose (for debuging)
 -L          Write names of changed files to /tmp/changed
 -N          No allocation mode. Only (old style) same length overwrites possible
See readme file on how to get to the registry files, and what they are.
Source/binary freely distributable under GPL v2 license. See README for details.
NOTE: This program is somewhat hackish! You are on your own!


```

Example Usage
-------
Mount  the Windows file system and enters the directory \WINDOWS\system32\config where Windows stores the SAM database.
```
ntfs-3g /dev/sda1 /media/win ; cd /media/win/WINDOWS/system32/config/
```
Opens registry hives SAM and system and change administrator account. This will work even if the name
has  been  changed  or  it  has been localized (since different language versions of NT use different
administrator names).
```
chntpw SAM system
```
Lists the users defined in the SAM registry file.
```
chntpw -l SAM
```   
Prompts for password for jabbathehutt and changes it in the SAM registry file, if found (otherwise do nothing).
```   
chntpw -u jabbathehutt SAM
```   



Links
-------

