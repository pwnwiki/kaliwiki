# readpst

Notes
-------
readpst is a program that can read an Outlook PST (Personal Folders) file and convert it into an mbox file, a format suitable for KMail, a recursive mbox structure, or separate emails.


Help Text
-------
```
ReadPST / LibPST v0.6.54
Little Endian implementation being used.
Usage: readpst [OPTIONS] {PST FILENAME}
OPTIONS:
	-V	- Version. Display program version
	-C charset	- character set for items with unspecified character set
	-D	- Include deleted items in output
	-M	- Write emails in the MH (rfc822) format
	-S	- Separate. Write emails in the separate format
	-b	- Don't save RTF-Body attachments
	-c[v|l]	- Set the Contact output mode. -cv = VCard, -cl = EMail list
	-d <filename> 	- Debug to file.
	-e	- As with -M, but include extensions on output files
	-h	- Help. This screen
	-j <integer>	- Number of parallel jobs to run
	-k	- KMail. Output in kmail format
	-o <dirname>	- Output directory to write files to. CWD is changed *after* opening pst file
	-q	- Quiet. Only print error messages
	-r	- Recursive. Output in a recursive format
	-t[eajc]	- Set the output type list. e = email, a = attachment, j = journal, c = contact
	-u	- Thunderbird mode. Write two extra .size and .type files
	-w	- Overwrite any output mbox files

Only one of -k -M -r -S should be specified

```

Example Usage
-------
See [1]

Links
-------
[1] http://www.question-defense.com/2012/11/29/readpst-backtrack-5-forensics-forensics-analysis-tools-readpst
