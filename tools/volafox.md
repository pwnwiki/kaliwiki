# volafox

Notes
-------
volafox: Mac OS X Memory Analysis Toolkit

Help Text
-------
```
volafox: Mac OS X Memory Analysis Toolkit
project: http://code.google.com/p/volafox
support: 10.6-8; 32/64-bit kernel
  input: *.vmem (VMWare memory file), *.mmr (Mac Memory Reader, flattened x86, IA-32e)
  usage: python /usr/bin/volafox -i IMAGE [-o COMMAND [-vp PID][-x PID][-x KEXT_ID][-x TASKID]]

Options:
-o CMD            : Print kernel information for CMD (below)
-p PID            : List open files for PID (where CMD is "lsof")
-v                : Print all files, including unsupported types (where CMD is "lsof")
-x PID/KID/TASKID : Dump process/task/kernel extension address space for PID/KID/Task ID (where CMD is "ps"/"kextstat"/"tasks")

COMMANDS:
system_profiler : Kernel version, CPU, and memory spec, Boot/Sleep/Wakeup time
mount           : Mounted filesystems
kextstat        : KEXT (Kernel Extensions) listing
ps              : Process listing
tasks           : Task listing (& Matching Process List)
systab          : Syscall table (Hooking Detection)
mtt             : Mach trap table (Hooking Detection)
netstat         : Network socket listing (Hash table)
lsof            : Open files listing by process (research, osxmem@gmail.com)
pestate         : Show Boot information (experiment)
efiinfo         : EFI System Table, EFI Runtime Services(experiment)
keychaindump    : Dump master key candidates for decrypting keychain(Lion, ML)


```

Example Usage
-------

Links
-------
[1] https://code.google.com/p/volafox/
