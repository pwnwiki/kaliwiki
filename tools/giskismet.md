# giskismet

Notes
-------
GISKismet is a wireless recon visualization tool to represent data gathered using Kismet in a flexible manner. GISKismet stores the information in a database so that the user can generate graphs using SQL.
GISKismet currently uses SQLite for the database and GoogleEarth / KML files for graphing. 


Help Text
-------
```
Usage: giskismet [Options]

Input File:
       --csv <csv-file>             Parse the input from Kismet-devel CSV
   -x  --xml <xml-file>             Parse the input from Kismet-newcore NETXML

Input Filters: 
       --bssid file | list          Filter based on BSSID     
       --essid file | list          Filter based on ESSID 
       --encryption file | list     Filter based on Encryption 
       --channel file | list        Filter based on Channel

file | list (list = comma separated lists(needs quotes)

Kismet-newcore Options:
   -a  --ap                         Insert only the APs

Query
   -q  --query [sql]                SQL query
   -m  --manual [csv]               CSV output of manual SQL query

   -o  --output [file]              Output filename
   -n  --name [str]                 Name of the KML layer
       --desc [str]                 Description of the KML layer

General Options:                
       --ignore-gps                 Import data even when GPS fields are missing
       --database [file]            SQLite3 database name [default: wireless.dbl]
   -d  --debug [num]                Display debug information
   -s  --silent                     No output when adding APs
   -v  --version                    Display version
   -h  --help                       Display this information

Send Comments to Joshua "Jabra" Abraham ( jabra@spl0it.org )

```

Example Usage
-------


```

```

Links
-------
[The Official GISKismet Development Home ](http://trac.assembla.com/giskismet/)
