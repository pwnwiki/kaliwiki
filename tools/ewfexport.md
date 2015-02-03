# ewfexport

Notes
-------
ewfexport is a utility to export media data stored in EWF files.
ewfexport is part of the libewf package.  libewf is a library to access the Expert Witness Compression Format (EWF).


Help Text
-------
```
ewfexport 20130416

Use ewfexport to export data from the EWF format (Expert Witness Compression
Format) to raw data or another EWF format.

Usage: ewfexport [ -A codepage ] [ -b number_of_sectors ]
                 [ -B number_of_bytes ] [ -c compression_values ]
                 [ -d digest_type ] [ -f format ] [ -l log_filename ]
                 [ -o offset ] [ -p process_buffer_size ]
                 [ -S segment_file_size ] [ -t target ] [ -hqsuvVw ] ewf_files

	ewf_files: the first or the entire set of EWF segment files

	-A:        codepage of header section, options: ascii (default),
	           windows-874, windows-932, windows-936, windows-949,
	           windows-950, windows-1250, windows-1251, windows-1252,
	           windows-1253, windows-1254, windows-1255, windows-1256,
	           windows-1257 or windows-1258
	-b:        specify the number of sectors to read at once (per chunk),
	           options: 16, 32, 64 (default), 128, 256, 512, 1024, 2048,
	           4096, 8192, 16384 or 32768 (not used for raw and files
	           formats)
	-B:        specify the number of bytes to export (default is all bytes)
	-c:        specify the compression values as: level or method:level
	           compression method options: deflate (default), bzip2
	           (bzip2 is only supported by EWF2 formats)
	           compression level options: none (default), empty-block,
	           fast or best
	-d:        calculate additional digest (hash) types besides md5,
	           options: sha1, sha256 (not used for raw and files format)
	-f:        specify the output format to write to, options:
	           raw (default), files (restricted to logical volume files), ewf,
	           smart, encase1, encase2, encase3, encase4, encase5, encase6,
	           encase7, encase7-v2, linen5, linen6, linen7, ewfx
	-h:        shows this help
	-l:        logs export errors and the digest (hash) to the log_filename
	-o:        specify the offset to start the export (default is 0)
	-p:        specify the process buffer size (default is the chunk size)
	-q:        quiet shows minimal status information
	-s:        swap byte pairs of the media data (from AB to BA)
	           (use this for big to little endian conversion and vice
	           versa)
	-S:        specify the segment file size in bytes (default is 1.4 GiB)
	           (minimum is 1.0 MiB, maximum is 7.9 EiB for raw, encase6
	           and encase7 format and 1.9 GiB for other formats)
	           (not used for files format)
	-t:        specify the target file to export to, use - for stdout
	           (default is export) stdout is only supported for the raw
	           format
	-u:        unattended mode (disables user interaction)
	-v:        verbose output to stderr
	-V:        print version
	-w:        zero sectors on checksum error (mimic EnCase like behavior)


```

Example Usage
-------

Links
-------

