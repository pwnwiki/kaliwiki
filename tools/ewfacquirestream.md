# ewfacquirestream

Notes
-------
ewfacquirestream is a utility to acquire media data from stdin and store it in EWF format (Expert Witness Format).  ewfacquirestream acquires media data in a format equivalent to EnCase and FTK imager, including meta data.Under Linux, FreeBSD, NetBSD, OpenBSD, MacOS-X/Darwin

ewfacquirestream is part of the libewf package.  libewf is a library to access the Expert Witness Compression Format (EWF).


Help Text
-------
```
ewfacquirestream 20130416

Use ewfacquirestream to acquire data from a pipe and store it in the EWF format
(Expert Witness Compression Format).

Usage: ewfacquirestream [ -A codepage ] [ -b number_of_sectors ]
                        [ -B number_of_bytes ] [ -c compression_values ]
                        [ -C case_number ] [ -d digest_type ]
                        [ -D description ] [ -e examiner_name ]
                        [ -E evidence_number ] [ -f format ]
                        [ -l log_filename ] [ -m media_type ]
                        [ -M media_flags ] [ -N notes ]
                        [ -o offset ] [ -p process_buffer_size ]
                        [ -P bytes_per_sector ] [ -S segment_file_size ]
                        [ -t target ] [ -2 secondary_target ]
                        [ -hqsvV ]

	Reads data from stdin

	-A: codepage of header section, options: ascii (default),
	    windows-874, windows-932, windows-936, windows-949,
	    windows-950, windows-1250, windows-1251, windows-1252,
	    windows-1253, windows-1254, windows-1255, windows-1256,
	    windows-1257 or windows-1258
	-b: specify the number of sectors to read at once (per chunk), options:
	    16, 32, 64 (default), 128, 256, 512, 1024, 2048, 4096, 8192, 16384
	    or 32768
	-B: specify the number of bytes to acquire (default is all bytes)
	-c: specify the compression values as: level or method:level
	    compression method options: deflate (default), bzip2
	    (bzip2 is only supported by EWF2 formats)
	    compression level options: none (default), empty-block,
	    fast or best
	-C: specify the case number (default is case_number).
	-d: calculate additional digest (hash) types besides md5, options:
	    sha1, sha256
	-D: specify the description (default is description).
	-e: specify the examiner name (default is examiner_name).
	-E: specify the evidence number (default is evidence_number).
	-f: specify the EWF file format to write to, options: ftk, encase2,
	    encase3, encase4, encase5, encase6 (default), encase7, linen5,
	    linen6, linen7, ewfx
	-h: shows this help
	-l: logs acquiry errors and the digest (hash) to the log_filename
	-m: specify the media type, options: fixed (default), removable,
	    optical, memory
	-M: specify the media flags, options: logical, physical (default)
	-N: specify the notes (default is notes).
	-o: specify the offset to start to acquire (default is 0)
	-p: specify the process buffer size (default is the chunk size)
	-P: specify the number of bytes per sector (default is 512)
	-q: quiet shows minimal status information
	-s: swap byte pairs of the media data (from AB to BA)
	    (use this for big to little endian conversion and vice versa)
	-S: specify the segment file size in bytes (default is 1.4 GiB)
	    (minimum is 1.0 MiB, maximum is 7.9 EiB for encase6 and
	    encase7 format and 1.9 GiB for other formats)
	-t: specify the target file (without extension) to write to (default
	    is image)
	-v: verbose output to stderr
	-V: print version
	-2: specify the secondary target file (without extension) to write to


```

Example Usage
-------

Links
-------

