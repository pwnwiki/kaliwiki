# chntpw

Notes
-------
This  manual page documents briefly the chntpw command. This manual page was written for the Debian distribution because the original program does not have a manual page.

chntpw is a utility to view some information and change user passwords in a Windows NT/2000 SAM userdatabase file, usually located at \WINDOWS\system32\config\SAM on the Windows file system. It is not necessary to
know the old passwords to reset them. In addition it contains a simple registry editor (same size data writes) and hex-editor with which the information contained in a registry file can be browsed and modified.


This little program will enable you to view some information and
change user passwords, change user/group memberships
in a Windows (NT/XP/Vista/win7/win8) etc SAM userdatabase file.
You do not need to know the old passwords.
However, you need to get at the registry files some way or another yourself.
In addition it contains a simple registry editor with full write support,
and hex-editor which enables you to
fiddle around with bits&bytes in the file as you wish yourself.[1]

```
chntpw: Program for interactively resetting passwords and group
memberships.
My boot CD runs this with options -i -L SAM

  chntpw: change password of a user in a Windows SAM file,
  or invoke registry editor. Should handle both 32 and 64 bit windows and
  all version from NT3.x to Win8
  chntpw [OPTIONS] <samfile> [systemfile] [securityfile] [otherreghive] [...]
   -h          This message
   -u <user>   Username or RID (0x3e9 for example) to interactively edit
   -l          list all users in SAM file and exit
   -i          Interactive Menu system
   -f          Interactively edit first admin user
   -e          Registry editor. Now with full write support!
   -d          Enter buffer debugger instead (hex editor), 
   -v          Be a little more verbose (for debuging)
   -L          For scripts, write names of changed files to /tmp/changed
   -N          No allocation mode. Only same length overwrites possible (very safe mode)
   -E          No expand mode, do not expand hive file (safe mode)



 -u <user>   Username or RID (0x3e9 for example) to interactively edit

Invoke the interactive edit menu on specified user.
Specifying a user name will most likely fail if user has international
character, so better to use user ID (RID), for example
 chnptw -u 0x3e9 SAM
to edit user with hexadecimal RID 3e9


 -l          list all users in SAM file and exit

Just that, list users in human readable form, with some info about if
user is admin and if password is set.

 -i          Interactive Menu system

Invokes the menu system. Menu items will vary a bit depending on what
registry hives are loaded.

 -f          Interactively edit first admin user

Select first admin user for edit. This is user with lowest RID that
also is member of administators group, or built-in user 0x1f4 if not
others possible.

 -e          Registry editor. Now with full write support!

Enter the registry editor. It is a small command system. ? for help
there. See other documentation for more on regedits.

 -d          Enter buffer debugger instead (hex editor), 

Command line type hex editor, mostly for debugging purposes. ? for help.

 -v          Be a little more verbose (for debuging)

Lots of debug output during most operations (especially hive loading)

 -L          For scripts, write names of changed files to /tmp/changed

If any of the other functions changes the registry, the changed files
are listed here. Can be used by wrapper scripts to know what to save.
My boot CD uses it.

 -N          No allocation mode. Only same length overwrites possible (very safe mode)

Safe mode. Will only allow changes in registry that overwrites old
values with same length data. Password reset only changes 2 bytes, and
does not change value lenght, so password reset will still work in
this safe mode. If something tries to violate this safe mode, a lot of
error messages (some of the rather obscure) may occur.

 -E          No expand mode, do not expand hive file (safe mode)

Safe mode. Does not allow expanding the size of the file, but will
allow adding keys/values as long as there is free space in the file
already. (most files contains some free space)
If expansion is needed but not allowed by this option,
a lot of obscure error messages may occur, and file should not be saved.
```

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
 1. [pogostick.net](http://pogostick.net/~pnh/ntpasswd/)
 
 2. [chntpw Wikipedia article](http://en.wikipedia.org/wiki/Chntpw)
 
 3. [Ubuntu Trusty manpage](http://manpages.ubuntu.com/manpages/trusty/en/man8/chntpw.8.html)
 
