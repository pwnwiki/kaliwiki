# volatility

Notes
-------
Volatility is a mighty tool for memory analysis. Find some tutorials in the "Links" section to get started.

Help Text
-------
```
Volatility Foundation Volatility Framework 2.3.1
Usage: Volatility - A memory forensics analysis platform.

Options:
  -h, --help            list all available options and their default values.
                        Default values may be set in the configuration file
                        (/etc/volatilityrc)
  --conf-file=/root/.volatilityrc
                        User based configuration file
  -d, --debug           Debug volatility
  --plugins=PLUGINS     Additional plugin directories to use (colon separated)
  --info                Print information about all registered objects
  --cache-directory=/root/.cache/volatility
                        Directory where cache files are stored
  --cache               Use caching
  --tz=TZ               Sets the timezone for displaying timestamps
  -f FILENAME, --filename=FILENAME
                        Filename to use when opening an image
  --profile=WinXPSP2x86
                        Name of the profile to load
  -l LOCATION, --location=LOCATION
                        A URN location from which to load an address space
  -w, --write           Enable write support
  --dtb=DTB             DTB Address
  --output=text         Output in this format (format support is module
                        specific)
  --output-file=OUTPUT_FILE
                        write output in this file
  -v, --verbose         Verbose information
  --shift=SHIFT         Mac KASLR shift address
  -g KDBG, --kdbg=KDBG  Specify a specific KDBG virtual address
  -k KPCR, --kpcr=KPCR  Specify a specific KPCR address

	Supported Plugin Commands:

		apihooks       	Detect API hooks in process and kernel memory
		atoms          	Print session and window station atom tables
		atomscan       	Pool scanner for _RTL_ATOM_TABLE
		bioskbd        	Reads the keyboard buffer from Real Mode memory
		callbacks      	Print system-wide notification routines
		clipboard      	Extract the contents of the windows clipboard
		cmdscan        	Extract command history by scanning for _COMMAND_HISTORY
		connections    	Print list of open connections [Windows XP and 2003 Only]
		connscan       	Scan Physical memory for _TCPT_OBJECT objects (tcp connections)
		consoles       	Extract command history by scanning for _CONSOLE_INFORMATION
		crashinfo      	Dump crash-dump information
		deskscan       	Poolscaner for tagDESKTOP (desktops)
		devicetree     	Show device tree
		dlldump        	Dump DLLs from a process address space
		dlllist        	Print list of loaded dlls for each process
		driverirp      	Driver IRP hook detection
		driverscan     	Scan for driver objects _DRIVER_OBJECT 
		dumpcerts      	Dump RSA private and public SSL keys
		dumpfiles      	Extract memory mapped and cached files
		envars         	Display process environment variables
		eventhooks     	Print details on windows event hooks
		evtlogs        	Extract Windows Event Logs (XP/2003 only)
		filescan       	Scan Physical memory for _FILE_OBJECT pool allocations
		gahti          	Dump the USER handle type information
		gditimers      	Print installed GDI timers and callbacks
		gdt            	Display Global Descriptor Table
		getservicesids 	Get the names of services in the Registry and return Calculated SID
		getsids        	Print the SIDs owning each process
		handles        	Print list of open handles for each process
		hashdump       	Dumps passwords hashes (LM/NTLM) from memory
		hibinfo        	Dump hibernation file information
		hivedump       	Prints out a hive
		hivelist       	Print list of registry hives.
		hivescan       	Scan Physical memory for _CMHIVE objects (registry hives)
		hpakextract    	Extract physical memory from an HPAK file
		hpakinfo       	Info on an HPAK file
		idt            	Display Interrupt Descriptor Table
		iehistory      	Reconstruct Internet Explorer cache / history
		imagecopy      	Copies a physical address space out as a raw DD image
		imageinfo      	Identify information for the image 
		impscan        	Scan for calls to imported functions
		kdbgscan       	Search for and dump potential KDBG values
		kpcrscan       	Search for and dump potential KPCR values
		ldrmodules     	Detect unlinked DLLs
		lsadump        	Dump (decrypted) LSA secrets from the registry
		machoinfo      	Dump Mach-O file format information
		malfind        	Find hidden and injected code
		mbrparser      	Scans for and parses potential Master Boot Records (MBRs) 
		memdump        	Dump the addressable memory for a process
		memmap         	Print the memory map
		messagehooks   	List desktop and thread window message hooks
		mftparser      	Scans for and parses potential MFT entries 
		moddump        	Dump a kernel driver to an executable file sample
		modscan        	Scan Physical memory for _LDR_DATA_TABLE_ENTRY objects
		modules        	Print list of loaded modules
		mutantscan     	Scan for mutant objects _KMUTANT 
		patcher        	Patches memory based on page scans
		printkey       	Print a registry key, and its subkeys and values
		privs          	Display process privileges
		procexedump    	Dump a process to an executable file sample
		procmemdump    	Dump a process to an executable memory sample
		pslist         	Print all running processes by following the EPROCESS lists 
		psscan         	Scan Physical memory for _EPROCESS pool allocations
		pstree         	Print process list as a tree
		psxview        	Find hidden processes with various process listings
		raw2dmp        	Converts a physical memory sample to a windbg crash dump
		screenshot     	Save a pseudo-screenshot based on GDI windows
		sessions       	List details on _MM_SESSION_SPACE (user logon sessions)
		shellbags      	Prints ShellBags info
		shimcache      	Parses the Application Compatibility Shim Cache registry key
		sockets        	Print list of open sockets
		sockscan       	Scan Physical memory for _ADDRESS_OBJECT objects (tcp sockets)
		ssdt           	Display SSDT entries
		strings        	Match physical offsets to virtual addresses (may take a while, VERY verbose)
		svcscan        	Scan for Windows services
		symlinkscan    	Scan for symbolic link objects 
		thrdscan       	Scan physical memory for _ETHREAD objects
		threads        	Investigate _ETHREAD and _KTHREADs
		timeliner      	Creates a timeline from various artifacts in memory 
		timers         	Print kernel timers and associated module DPCs
		unloadedmodules	Print list of unloaded modules
		userassist     	Print userassist registry keys and information
		userhandles    	Dump the USER handle tables
		vaddump        	Dumps out the vad sections to a file
		vadinfo        	Dump the VAD info
		vadtree        	Walk the VAD tree and display in tree format
		vadwalk        	Walk the VAD tree
		vboxinfo       	Dump virtualbox information
		vmwareinfo     	Dump VMware VMSS/VMSN information
		volshell       	Shell in the memory image
		windows        	Print Desktop Windows (verbose details)
		wintree        	Print Z-Order Desktop Windows Tree
		wndscan        	Pool scanner for tagWINDOWSTATION (window stations)
		yarascan       	Scan process or kernel memory with Yara signatures


```

Example Usage
-------
To execute volatility use the command "vol".

Links
-------
[1] https://code.google.com/p/volatility/
[2] http://resources.infosecinstitute.com/memory-forensics-and-analysis-using-volatility/
[3] http://www.evild3ad.com/956/volatility-memory-forensics-basic-usage-for-malware-analysis/
