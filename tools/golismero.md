# golismero.py

Notes
-------

Help Text
-------
```
/----------------------------------------------\
| GoLismero 2.0.0b3 - The Web Knife            |
| Contact: golismero.project<@>gmail.com       |
|                                              |
| Daniel Garcia Garcia a.k.a cr0hn (@ggdaniel) |
| Mario Vilas (@Mario_Vilas)                   |
\----------------------------------------------/

usage: golismero.py COMMAND [TARGETS...] [--options]

  SCAN:
    Perform a vulnerability scan on the given targets. Optionally import
    results from other tools and write a report. The arguments that follow may
    be domain names, IP addresses or web pages.

  PROFILES:
    Show a list of available config profiles. This command takes no arguments.

  PLUGINS:
    Show a list of available plugins. This command takes no arguments.

  INFO:
    Show detailed information on a given plugin. The arguments that follow are
    the plugin IDs. You can use glob-style wildcards.

  REPORT:
    Write a report from an earlier scan. This command takes no arguments.
    To specify output files use the -o switch.

  IMPORT:
    Import results from other tools and optionally write a report, but don't
    scan the targets. This command takes no arguments. To specify input files
    use the -i switch.

  DUMP:
    Dump the database from an earlier scan in SQL format. This command takes no
    arguments. To specify output files use the -o switch.

  UPDATE:
    Update GoLismero to the latest version. Requires Git to be installed and
    available in the PATH. This command takes no arguments.

examples:

  scan a website and show the results on screen:
    golismero.py scan http://www.example.com

  grab Nmap results, scan all hosts found and write an HTML report:
    golismero.py scan -i nmap_output.xml -o report.html

  grab results from OpenVAS and show them on screen, but don't scan anything:
    golismero.py import -i openvas_output.xml

  show a list of all available configuration profiles:
    golismero.py profiles

  show a list of all available plugins:
    golismero.py plugins

  show information on all bruteforcer plugins:
    golismero.py info brute_*

  dump the database from a previous scan:
    golismero.py dump -db example.db -o dump.sql

```

Example Usage
-------

Links
-------

http://golismero-project.com/
https://github.com/golismero/golismero
