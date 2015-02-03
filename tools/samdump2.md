# samdump2

Notes
-------
This tool is designed to dump Windows 2k/NT/XP password hashes from a SAM file, using the syskey bootkey from the system hive.

This package also provides the functionality of bkhive, which recovers the syskey bootkey from a Windows NT/2K/XP system hive.

Syskey is a Windows feature that adds an additional encryption layer to the password hashes stored in the SAM database.


Help Text
-------
```
samdump2 1.1.1 by Objectif Securite
http://www.objectif-securite.ch
original author: ncuomo@studenti.unina.it

Usage:
samdump2 samhive keyfile
```

Example Usage
-------
Stolen from epyxforensics

We need to extract the syskey out of the SYSTEM hive.  The syskey is a utility that encrypts the hashed password information in the SAM hive.  We are going to use the program bkhive and we are going to point it to the SYSTEM hive so that we can extract that key.  The SYSTEM hive is located in “Windows/System32/config/”  In our setup, I will have to navigate to my windows partition, I will use the following command to tell bkhive to look at the SYSTEM hive and extract the syskey into a txt file appropriately named syskey.txt into our current directory (which if you remember is the Test folder, located on the Desktop).  
```
bkhive /media/8ADCBB5EDCBB42ED/Windows/System32/config/SYSTEM syskey.txt 
```

After pressing enter, if everything worked, you should have received the following: 

```
carlos@XPS-M1330:~/Desktop/Test$ bkhive /media/8ADCBB5EDCBB42ED/Windows/System32/config/SYSTEM syskey.txt
bkhive 1.1.1 by Objectif Securite
http://www.objectif-securite.choriginal author: ncuomo at studenti.unina.it
Root Key : CMI-CreateHive{2A7FB991-7BBE-4F9D-B91E-7CB51D4737F5}
Default ControlSet: 001Bootkey: 90bb26a726a7bf1150f2edf4acb8382b
carlos@XPS-M1330:~/Desktop/Test$ 
```

Lets see if we have a file named syskey.txt in our current directory.  For that we will use the LS command, which stands for list (files).  Type “ls” and press enter. 

```
carlos@XPS-M1330:~/Desktop/Test$ ls
syskey.txt
carlos@XPS-M1330:~/Desktop/Test$ 
```

Notice that we are in the Test Directory and Yes, we do have a txt file in our directory named syskey.txt.  You can open the file with a text editor and you will see unreadable characters.

Now we are going to use the program samdump2 to point it to both the SAM hive and the syskey.txt file so that it can use the syskey and extract the hashed passwords out of the SAM hive into our current directory, into a file appropriately named hashes.txt.  We will accomplish this with the following command.

```
samdump2 /media/8ADCBB5EDCBB42ED/Windows/System32/config/SAM syskey.txt > hashes.txt
```

After pressing enter, if everything worked, you should have received the following:

```
carlos@XPS-M1330:~/Desktop/Test$ samdump2 /media/8ADCBB5EDCBB42ED/Windows/System32/config/SAM syskey.txt > hashes.txt
samdump2 1.1.1 by Objectif Securite
http://www.objectif-securite.ch
original author: ncuomo at studenti.unina.it
Root Key : CMI-CreateHive{C4E7BA2B-68E8-499C-B1A1-371AC8D717C7}
carlos@XPS-M1330:~/Desktop/Test$
```

Lets see if we have a file named hashes.txt in our current directory.  For that we will again use the LS command.  Type ls and press enter.

```
carlos@XPS-M1330:~/Desktop/Test$ ls
hashes.txt  syskey.txt
carlos@XPS-M1330:~/Desktop/Test$
```

Notice that we are still in the Test directory and Yes, we do have a txt file in our directory named hashes.txt along with the syskey.txt.  You can now open the hashes.txt file with a text editor.  Once opened, you will see a password hashdump for all of the users stored inside of the SAM hive.  We are only interested in the previously created user profile that we called Test.  Below is Test's hashdump.

```
Test:1003:aad3b435b51404eeaad3b435b51404ee:9b600b4e30254213f574bc7449524c12:::
```

The 32 character alphanumerical word, after the colon is the the hash of the Test user password (9b600b4e30254213f574bc7449524c12).  To crack the hash, find one of the many websites that offer free hash decrypting.  For the purposes of this article, I used www.xdecrypt dot com.  Go to www.xdecrypt dot com and paste the hash into the top box.  Click on the “decrypter” button, and wait for the results.  Xdecrypt had this hash stored and provided us with the translation of this hash back into plain text. 

```
9b600b4e30254213f574bc7449524c12(ntlm)=Forensics1
```

Links
-------
* [irongeek video](http://www.irongeek.com/i.php?page=videos/samdump2auditor)
* [irongeek link](http://www.irongeek.com/i.php?page=security/cracking-windows-vista-xp-2000-nt-passwords-via-sam-and-syskey-with-cain-ophcrack-saminside-bkhive-etc)
* [expyforensics](http://epyxforensics.com/node/34)