# mfcuk

Notes
-------
MFCUK - MiFare Classic Universal toolKit
Toolkit containing samples and various tools based on and around libnfc and crapto1, with emphasis on Mifare Classic NXP/Philips RFID cards


Help Text
-------
```
mfcuk - 0.3.8
Mifare Classic DarkSide Key Recovery Tool - 0.3
by Andrei Costin, zveriu@gmail.com, http://andreicostin.com

Usage:
-C - require explicit connection to the reader. Without this option, the connection is not made and recovery will not occur
-i mifare.dmp - load input mifare_classic_tag type dump
-I mifare_ext.dmp - load input extended dump specific to this tool, has several more fields on top of mifare_classic_tag type dump
-o mifare.dmp - output the resulting mifare_classic_tag dump to a given file
-O mifare_ext.dmp - output the resulting extended dump to a given file
-V sector[:A/B/any_other_alphanum[:fullkey]] - verify key for specified sector, -1 means all sectors
	After first semicolon key-type can specified: A verifies only keyA, B verifies only keyB, anything else verifies both keys
	After second semicolon full 12 hex-digits key can specified - this key will override any loaded dump key for the given sector(s) and key-type(s)
-R sector[:A/B/any_other_alphanum] - recover key for sector, -1 means all sectors.
	After first semicolon key-type can specified: A recovers only keyA, B recovers only keyB, anything else recovers both keys
-U UID - force specific UID. If a dump was loaded with -i, -U will overwrite the in the memory where dump was loaded
-M tagtype - force specific tagtype. 8 is 1K, 24 is 4K, 32 is DESFire
-D - for sectors and key-types marked for verification, in first place use default keys to verify (maybe you are lucky)
-d key - specifies additional full 12 hex-digits default key to be checked. Multiple -d options can be used for more additional keys
-s - milliseconds to sleep for SLEEP_AT_FIELD_OFF (Default: 10 ms)
-S - milliseconds to sleep for SLEEP_AFTER_FIELD_ON (Default: 50 ms)
-P hex_literals_separated - try to recover the key from a conversation sniffed with Proxmark3 (mifarecrack.c based). Accepts several options:
	Concatenated string in hex literal format of form uid:tag_chal:nr_enc:reader_resp:tag_resp
	Example -P 0x5c72325e:0x50829cd6:0xb8671f76:0xe00eefc9:0x4888964f would find key FFFFFFFFFFFF
-p proxmark3_full.log - tries to parse the log file on it's own (mifarecrack.py based), get the values for option -P and invoke it
-F - tries to fingerprint the input dump (-i) against known cards' data format
-v verbose_level - verbose level (default is O)

Usage examples:
  Recove all keys from all sectors:
    mfcuk -C -R -1
  Recove the sector #0 key with 250 ms for all delays (delays could give more results): 
    mfcuk -C -R 0 -s 250 -S 250

```

Example Usage
-------


```

```

Links
-------
[Mfcuk Google Code project](https://code.google.com/p/mfcuk/)
