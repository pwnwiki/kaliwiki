# dc3dd 

Notes
-------
dc3dd is a patched version of GNU dd with added features for computer forensics. It was developed at the DoD Cyber Crime Center by Jesse Kornblum. The first release, corresponding to Coreutils version 6.9.91, was published on 1 Feb 2008.[1]

Help Text
-------
```
------
usage:
------

	dc3dd [OPTION 1] [OPTION 2] ... [OPTION N]

		*or*

	dc3dd [HELP OPTION]

	where each OPTION is selected from the basic or advanced
	options listed below, or HELP OPTION is selected from the
	help options listed below.

--------------
basic options:
--------------

	if=DEVICE or FILE    Read input from a device or a file (see note #1
	                     below for how to read from standard input). This
	                     option can only be used once and cannot be
	                     combined with ifs=, pat=, or tpat=.
	ifs=BASE.FMT         Read input from a set of files with base name
	                     BASE and sequential file name extensions
	                     conforming to the format specifier FMT (see note
	                     #4 below for how to specify FMT). This option
	                     can only be used once and cannot be combined with
	                     if=, pat=, or tpat=.
	of=FILE or DEVICE    Write output to a file or device (see note #2
	                     below for how to write to standard output). This
	                     option can be used more than once (see note #3
	                     below for how to generate multiple outputs).
	hof=FILE or DEVICE   Write output to a file or device, hash the
	                     output file or device, and verify by comparing
	                     the output hash(es) to the input hash(es). This
	                     option can be used more than once (see note #3
	                     below for how to generate multiple outputs).
	ofs=BASE.FMT         Write output to a set of files with base name BASE
	                     and sequential file name extensions generated from
	                     the format specifier FMT (see note #4 below for
	                     how to specify FMT). This option can be used more
	                     than once (see note #3 below for how to generate
	                     multiple outputs). Specify the maximum size of
	                     each file in the set using ofsz=.
	hofs=BASE.FMT        Write output to a set of files with base name BASE
	                     and sequential file name extensions generated from
	                     the format specifier FMT (see note #4 below for
	                     how to specify FMT). Hash the output files and
	                     verify by comparing the output hash(es) to the
	                     input hash(es). This option can be used more than
	                     once (see note #3 below for how to generate
	                     multiple outputs). Specify the maximum size of
	                     each file in the set using ofsz=.
	ofsz=BYTES           Set the maximum size of each file in the sets of
	                     files specified using ofs= or hofs= to
	                     BYTES (see note #5 below). A default value for
	                     this option may be set at compile time using
	                     -DDEFAULT_OUTPUT_FILE_SIZE followed by the desired
	                     value in BYTES.
	hash=ALGORITHM       Compute an ALGORITHM hash of the input and also
	                     of any outputs specified using hof=, hofs=, phod=,
	                     or fhod=, where ALGORITHM is one of md5, sha1,
	                     sha256, or sha512. This option may be used once
	                     for each supported ALGORITHM. Alternatively,
	                     hashing can be activated at compile time using one
	                     or more of -DDEFAULT_HASH_MD5,-DDEFAULT_HASH_SHA1,
	                     -DDEFAULT_HASH_SHA256, and -DDEFAULT_HASH_SHA512.
	log=FILE             Log I/O statistcs, diagnostics, and total hashes
	                     of input and output to FILE. If hlog= is not
	                     specified, piecewise hashes of multiple file
	                     input and output are also logged to FILE. This
	                     option can be used more than once to generate
	                     multiple logs.
	hlog=FILE            Log total hashes and piecewise hashes to FILE.
	                     This option can be used more than once to generate
	                     multiple logs.

-----------------
advanced options:
-----------------

	phod=DEVICE          The same as hof=DEVICE, except only the bytes
	                     written to DEVICE by dc3dd are verified. This
	                     option can be used more than once (see note
	                     #3 below for how to generate multiple outputs).
	fhod=DEVICE          The same as phod=DEVICE, with additional
	                     hashing of the entire output DEVICE. This option
	                     can be used more than once (see note #3 below
	                     for how to generate multiple outputs).
	rec=off              By default, zeros are written to the output(s) in
	                     place of bad sectors when the input is a device.
	                     Use this option to cause the program to instead
	                     exit when a bad sector is encountered.
	wipe=DEVICE          Wipe DEVICE by writing zeros (default) or a
	                     pattern specified by pat= or tpat=.
	hwipe=DEVICE         Wipe DEVICE by writing zeros (default) or a
	                     pattern specified by pat= or tpat=. Verify
	                     DEVICE after writing it by hashing it and
	                     comparing the hash(es) to the input hash(es).
	pat=HEX              Use pattern as input, writing HEX to every byte
	                     of the output. This option can only be used once
	                     and cannot be combined with if=, ifs=, or
	                     tpat=.
	tpat=TEXT            Use text pattern as input, writing the string TEXT
	                     repeatedly to the output. This option can only be
	                     used once and cannot be combined with if=, ifs=,
	                     or pat=.
	cnt=SECTORS          Read only SECTORS input sectors. Must be used
	                     with pat= or tpat= if not using the pattern with
	                     wipe= or hwipe= to wipe a device.
	iskip=SECTORS        Skip SECTORS sectors at start of the input device
	                     or file.
	oskip=SECTORS        Skip SECTORS sectors at start of the output
	                     file. Specifying oskip= automatically 
	                     sets app=on.
	app=on               Do not overwrite an output file specified with
	                     of= if it already exists, appending output instead.
	ssz=BYTES            Unconditionally use BYTES (see note #5 below) bytes
	                     for sector size. If ssz= is not specified,
	                     sector size is determined by probing the device;
	                     if the probe fails or the target is not a device,
	                     a sector size of 512 bytes is assumed.
	bufsz=BYTES          Set the size of the internal byte buffers to BYTES
	                     (see note #5 below). This effectively sets the
	                     maximum number of bytes that may be read at a time
	                     from the input. BYTES must be a multiple of sector
	                     size. Use this option to fine-tune performance.
	verb=on              Activate verbose reporting, where sectors in/out
	                     are reported for each file in sets of files
	                     specified using ifs=, ofs=, or hofs=.
	                     Alternatively, verbose reporting may be activated
	                     at compile time using -DDEFAULT_VERBOSE_REPORTING.
	nwspc=on             Activate compact reporting, where the use
	                     of white space to divide log output into
	                     logical sections is suppressed. Alternatively,
	                     compact reporting may be activated at compile
	                     time using -DDEFAULT_COMPACT_REPORTING.
	b10=on               Activate base 10 bytes reporting, where the
	                     progress display reports 1000 bytes instead
	                     of 1024 bytes as 1 KB. Alternatively, base 10
	                     bytes reporting may be activated at compile
	                     time using -DDEFAULT_BASE_TEN_BYTES_REPORTING.
	corruptoutput=on     For verification testing and demonstration
	                     purposes, corrupt the output file(s) with extra
	                     bytes so a hash mismatch is guaranteed.

-------------
help options:
-------------

      --help     display this help and exit
      --version  output version information and exit
      --flags    display compile-time flags and exit

------
notes:
------

1. To read from stdin, do not specify if=, ifs=, pat=, or tpat=.
2. To write to stdout, do not specify of=, hof=, ofs=, hofs=, phod=,
   fhod=, wipe=, or hwipe=.
3. To write to multiple outputs specify more than one of of=, hof=, ofs=,
   hofs=, phod=, or fhod=, in any combination.
4. FMT is a pattern for a sequence of file extensions that can be numerical
   starting at zero, numerical starting at one, or alphabetical. Specify FMT
   by using a series of zeros, ones, or a's, respectively. The number of
   characters used indicates the desired length of the extensions.
   For example, a FMT specifier of 1111 indicates four character
   numerical extensions starting with 0000.
5. BYTES may be followed by the following multiplicative suffixes:
   c (1), w (2), b (512), kB (1000), K (1024), MB (1000*1000),
   M (1024*1024), GB (1000*1000*1000), G (1024*1024*1024), and
   so on for T, P, E, Z, and Y.
6. Consider using cnt=, iskip= and oskip= to work around
   unreadable sectors if error recovery fails.
7. Sending an interrupt (e.g., CTRL+C) to dc3dd will cause
   the program to report the work completed at the time
   the interrupt is received and then exit.

Report bugs to <dc3dd@dc3.mil>.
dc3dd completed at 2014-04-22 14:11:52 -0500

```

Example Usage
-------

Links
-------
[1] http://www.forensicswiki.org/wiki/Dc3dd
