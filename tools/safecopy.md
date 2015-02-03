# safecopy

Notes
-------
A data recovery tool.

Safecopy  is  a data recovery tool which tries to extract as much data as possible from a seekable, but problematic (i.e. damaged sectors) source - like floppy drives, harddisk partitions, CDs, ...,
where other tools like dd would fail doe to I/O errors.

Safecopy tries to get as much data from the source as possible without device dependent tricks. For example to get an ISO image from a copy protected or otherwise damaged CD-ROM, cdrdao and  bin2iso
would possibly do a better and faster job.

Safecopy comes with preset options (named stages) to ease its use.  These presets can be overridden by individual options.


Help Text
-------
```
Safecopy 1.6 by CorvusCorax
Usage: safecopy [options] <source> <target>
Options:
	--stage1 : Preset to rescue most of the data fast,
	           using no retries and avoiding bad areas.
	           Presets: -f 10% -r 10% -R 1 -Z 0 -L 2 -M BaDbLoCk
	                    -o stage1.badblocks
	--stage2 : Preset to rescue more data, using no retries
	           but searching for exact ends of bad areas.
	           Presets: -f 128* -r 1* -R 1 -Z 0 -L 2
	                    -I stage1.badblocks
	                    -o stage2.badblocks
	--stage3 : Preset to rescue everything that can be rescued
	           using maximum retries, head realignment tricks
	           and low level access.
	           Presets: -f 1* -r 1* -R 4 -Z 1 -L 2
	                    -I stage2.badblocks
	                    -o stage3.badblocks
	All stage presets can be overridden by individual options.
	-b <size> : Blocksize for default read operations.
	            Set this to the physical sectorsize of your media.
	            Default: 1*
	            Hardware block size if reported by OS, otherwise 4096
	-f <size> : Blocksize when skipping over badblocks.
	            Higher settings put less strain on your hardware,
	            but you might miss good areas in between two bad ones.
	            Default: 16*
	-r <size> : Resolution in bytes when searching for the exact
	            beginning or end of a bad area.
	            If you read data directly from a device there is no
	            need to set this lower than the hardware blocksize.
	            On mounted filesystems however, read blocks
	            and physical blocks could be misaligned.
	            Smaller values lead to very thorough attempts to read
	            data at the edge of damaged areas,
	            but increase the strain on the damaged media.
	            Default: 1*
	-R <number> : At least that many read attempts are made on the first
	              bad block of a damaged area with minimum resolution.
	              More retries can sometimes recover a weak sector,
	              but at the cost of additional strain.
	              Default: 3
	-Z <number> : On each error, force seek the read head from start to
	              end of the source device as often as specified.
	              That takes time, creates additional strain and might
	              not be supported by all devices or drivers.
	              Default: 1
	-L <mode> : Use low level device calls as specified:
	                   0  Do not use low level device calls
	                   1  Attempt low level device calls
	                      for error recovery only
	                   2  Always use low level device calls
	                      if available
	            Supported low level features in this version are:
	                SYSTEM  DEVICE TYPE   FEATURE
	                Linux   cdrom/dvd     bus/device reset
	                Linux   cdrom         read sector in raw mode
	                Linux   floppy        controller reset, twaddle
	            Default: 1
	--sync : Use synchronized read calls (disable driver buffering).
	         Safecopy will use O_DIRECT if supported by the OS
	         and O_SYNC otherwise.
	         Default: Asynchronous read buffering by the OS is allowed
	-s <blocks> : Start position where to start reading.
	              Will correspond to position 0 in the destination file.
	              Default: block 0
	-l <blocks> : Maximum length of data to be read.
	              Default: Entire size of input file
	-I <badblockfile> : Incremental mode. Assume the target file already
	                    exists and has holes specified in the badblockfile.
	                    It will be attempted to retrieve more data from
	                    the listed blocks or from beyond the file size
	                    of the target file only.
	                    Warning: Without this option, the destination file
	                    will be emptied prior to writing.
	                    Use -I /dev/null if you want to continue a previous
	                    run of safecopy without a badblock list.
	                    Default: none
	-i <bytes> : Blocksize to interpret the badblockfile given with -I.
	             Default: Blocksize as specified by -b
	-X <badblockfile> : Exclusion mode. If used together with -I,
	                    excluded blocks override included blocks.
	                    Safecopy will not read or write any data from
	                    areas covered by exclude blocks.
	                    Default: none
	-x <bytes> : Blocksize to interpret the badblockfile given with -X.
	             Default: Blocksize as specified by -b
	-o <badblockfile> : Write a badblocks/e2fsck compatible bad block file.
	                    Default: none
	-S <seekscript> : Use external script for seeking in input file.
	                  (Might be useful for tape devices and similar).
	                  Seekscript must be an executable that takes the
	                  number of blocks to be skipped as argv1 (1-64)
	                  the blocksize in bytes as argv2
	                  and the current position (in bytes) as argv3.
	                  Return value needs to be the number of blocks
	                  successfully skipped, or 0 to indicate seek failure.
	                  The external seekscript will only be used
	                  if lseek() fails and we need to skip over data.
	                  Default: none
	-M <string> : Mark unrecovered data with this string instead of
	              skipping it. This helps in later finding corrupted
	              files on rescued file system images.
	              The default is to zero unreadable data on creation
	              of output files, and leaving the data as it is
	              on any later run.
	              Warning: When used in combination with
	              incremental mode (-I) this may overwrite data
	              in any block that occurs in the -I file.
	              Blocks not in the -I file, or covered by the file
	              specified with -X are save from being overwritten.
	              Default: none
	--debug <level> : Enable debug output. Level is a bit field,
	                  add values together for more information:
	                     program flow:     1
	                     IO control:       2
	                     badblock marking: 4
	                     seeking:          8
	                     incremental mode: 16
	                     exclude mode:     32
	                  or for all debug output: 255
	                  Default: 0
	-T <timingfile> : Write sector read timing information into
	                  this file for later analysis.
	                  Default: none
	-h | --help : Show this text

Valid parameters for -f -r -b <size> options are:
	<integer>	Amount in bytes - i.e. 1024
	<percentage>%	Percentage of whole file/device size - e.g. 10%
	<number>*	-b only, number times blocksize reported by OS
	<number>*	-f and -r only, number times the value of -b

Description of output:
	. : Between 1 and 1024 blocks successfully read.
	_ : Read of block was incomplete. (possibly end of file)
	    The blocksize is now reduced to read the rest.
	|/| : Seek failed, source can only be read sequentially.
	> : Read failed, reducing blocksize to read partial data.
	! : A low level error on read attempt of smallest allowed size
	    leads to a retry attempt.
	[xx](+yy){ : Current block and number of bytes continuously
	             read successfully up to this point.
	X : Read failed on a block with minimum blocksize and is skipped.
	    Unrecoverable error, destination file is padded with zeros.
	    Data is now skipped until end of the unreadable area is reached.
	< : Successful read after the end of a bad area causes
	    backtracking with smaller blocksizes to search for the first
	    readable data.
	}[xx](+yy) : current block and number of bytes of recent
	             continuous unreadable data.

Copyright 2009 CorvusCorax
This is free software. You may redistribute copies of it under
the terms of the GNU General Public License version 2 or above.
	<http://www.gnu.org/licenses/gpl2.html>.
There is NO WARRANTY, to the extent permitted by law.


```

Example Usage
-------

Links
-------

