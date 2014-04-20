# padbuster

Notes
-------

Help Text
-------
```
+-------------------------------------------+
| PadBuster - v0.3.3                        |
| Brian Holyfield - Gotham Digital Science  |
| labs@gdssecurity.com                      |
+-------------------------------------------+
    
    Use: padBuster.pl URL EncryptedSample BlockSize [options]

  Where: URL = The target URL (and query string if applicable)
         EncryptedSample = The encrypted value you want to test. Must
                           also be present in the URL, PostData or a Cookie
         BlockSize = The block size being used by the algorithm

Options:
	 -auth [username:password]: HTTP Basic Authentication 
	 -bruteforce: Perform brute force against the first block 
	 -ciphertext [Bytes]: CipherText for Intermediate Bytes (Hex-Encoded)
         -cookies [HTTP Cookies]: Cookies (name1=value1; name2=value2)
         -encoding [0-4]: Encoding Format of Sample (Default 0)
                          0=Base64, 1=Lower HEX, 2=Upper HEX
                          3=.NET UrlToken, 4=WebSafe Base64
         -encodedtext [Encoded String]: Data to Encrypt (Encoded)
         -error [Error String]: Padding Error Message
         -headers [HTTP Headers]: Custom Headers (name1::value1;name2::value2)
	 -interactive: Prompt for confirmation on decrypted bytes
	 -intermediate [Bytes]: Intermediate Bytes for CipherText (Hex-Encoded)
	 -log: Generate log files (creates folder PadBuster.DDMMYY)
	 -noencode: Do not URL-encode the payload (encoded by default)
	 -noiv: Sample does not include IV (decrypt first block) 
         -plaintext [String]: Plain-Text to Encrypt
         -post [Post Data]: HTTP Post Data String
	 -prefix [Prefix]: Prefix bytes to append to each sample (Encoded) 
	 -proxy [address:port]: Use HTTP/S Proxy
	 -proxyauth [username:password]: Proxy Authentication
	 -resume [Block Number]: Resume at this block number
	 -usebody: Use response body content for response analysis phase
         -verbose: Be Verbose
         -veryverbose: Be Very Verbose (Debug Only)
         

```

Example Usage
-------

Links
-------

