# hash-identifier

Notes
-------
Software to identify the different types of hashes used to encrypt data and especially passwords.

Encryption formats supported:

* ADLER-32
* CRC-32
* CRC-32B
* CRC-16
* CRC-16-CCITT
* DES(Unix)
* FCS-16
* GHash-32-3
* GHash-32-5
* GOST R 34.11-94
* Haval-160
* Haval-192 110080 ,Haval-224 114080 ,Haval-256
* Lineage II C4
* Domain Cached Credentials
* XOR-32
* MD5(Half)
* MD5(Middle)
* MySQL
* MD5(phpBB3)
* MD5(Unix)
* MD5(Wordpress)
* MD5(APR)
* Haval-128
* MD2
* MD4
* MD5
* MD5(HMAC(Wordpress))
* NTLM
* RAdmin v2.x
* RipeMD-128
* SNEFRU-128
* Tiger-128
* MySQL5 - SHA-1(SHA-1($pass))
* MySQL 160bit - SHA-1(SHA-1($pass))
* RipeMD-160
* SHA-1
* SHA-1(MaNGOS)
* Tiger-160
* Tiger-192
* md5($pass.$salt) - Joomla
* SHA-1(Django)
* SHA-224
* RipeMD-256
* SNEFRU-256
* md5($pass.$salt) - Joomla
* SAM - (LM_hash:NT_hash)
* SHA-256(Django)
* RipeMD-320
* SHA-384
* SHA-256
* SHA-384(Django)
* SHA-512
* Whirlpool
* And more…

Help Text
-------
```
no help text
```

Example Usage
-------
Example using "password" run through sha-1

```
root@kali:~# hash-identifier
   #########################################################################
   #	 __  __ 		    __		 ______    _____	   #
   #	/\ \/\ \		   /\ \ 	/\__  _\  /\  _ `\	   #
   #	\ \ \_\ \     __      ____ \ \ \___	\/_/\ \/  \ \ \/\ \	   #
   #	 \ \  _  \  /'__`\   / ,__\ \ \  _ `\	   \ \ \   \ \ \ \ \	   #
   #	  \ \ \ \ \/\ \_\ \_/\__, `\ \ \ \ \ \	    \_\ \__ \ \ \_\ \	   #
   #	   \ \_\ \_\ \___ \_\/\____/  \ \_\ \_\     /\_____\ \ \____/	   #
   #	    \/_/\/_/\/__/\/_/\/___/    \/_/\/_/     \/_____/  \/___/  v1.1 #
   #								 By Zion3R #
   #							www.Blackploit.com #
   #						       Root@Blackploit.com #
   #########################################################################

   -------------------------------------------------------------------------
 HASH: 5baa61e4c9b93f3f0682250b6cf8331b7ee68fd8

Possible Hashs:
[+]  SHA-1
[+]  MySQL5 - SHA-1(SHA-1($pass))
```

Links
-------
[Google Code](https://code.google.com/p/hash-identifier/)
[Youtube Video](https://www.youtube.com/watch?v=EaoiZ2CnOLo)
