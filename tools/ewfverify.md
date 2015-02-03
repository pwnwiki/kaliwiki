# ewfverify

Notes
-------
ewfverify is a utility to verify media data stored in EWF files.
ewfverify is part of the libewf package.  libewf is a library to access the Expert Witness Compression Format (EWF).


Help Text
-------
```
ewfverify 20130416

Use ewfverify to verify data stored in the EWF format (Expert Witness
Compression Format).

Usage: ewfverify [ -A codepage ] [ -d digest_type ] [ -f format ]
                 [ -l log_filename ] [ -p process_buffer_size ]
                 [ -hqvVw ] ewf_files

	ewf_files: the first or the entire set of EWF segment files

	-A:        codepage of header section, options: ascii (default),
	           windows-874, windows-932, windows-936, windows-949,
	           windows-950, windows-1250, windows-1251, windows-1252,
	           windows-1253, windows-1254, windows-1255, windows-1256,
	           windows-1257 or windows-1258
	-d:        calculate additional digest (hash) types besides md5,
	           options: sha1, sha256
	-f:        specify the input format, options: raw (default),
	           files (restricted to logical volume files)
	-h:        shows this help
	-l:        logs verification errors and the digest (hash) to the
	           log_filename
	-p:        specify the process buffer size (default is the chunk size)
	-q:        quiet shows minimal status information
	-v:        verbose output to stderr
	-V:        print version
	-w:        zero sectors on checksum error (mimic EnCase like behavior)


```

Example Usage
-------

Links
-------

