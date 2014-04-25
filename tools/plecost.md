# plecost

Notes
-------

Help Text
-------
```
////////////////////////////////////////////
// ..................................DMI...
// .............................:MMMM......
// .........................$MMMMM:........
// .........M.....,M,=NMMMMMMMMD...........
// ........MMN...MMMMMMMMMMMM,.............
// .......MMMMMMMMMMMMMMMMM~...............
// .......MMMMMMMMMMMMMMM..................
// ....?MMMMMMMMMMMMMMMN$I.................
// .?.MMMMMMMMMMMMMMMMMMMMMM...............
// .MMMMMMMMMMMMMMN........................
// 7MMMMMMMMMMMMMON$.......................
// ZMMMMMMMMMMMMMMMMMM.......plecost.......
// .:MMMMMMMZ~7MMMMMMMMMO..................
// ....~+:.................................
//
// Plecost - Wordpress finger printer Tool (with threads support) 0.2.2-9-beta
//        
// Developed by:
//        Francisco Jesus Gomez aka (ffranz@iniqua.com)
//        Daniel Garcia Garcia (dani@iniqua.com)
// 
// Info: http://iniqua.com/labs/
// Bug report: plecost@iniqua.com
        
        
Usage: /usr/bin/plecost [options] [ URL | [-l num] -G]


Google search options:
    -l num    : Limit number of results for each plugin in google.
    -G        : Google search mode
    
Options:
    -n        : Number of plugins to use (Default all - more than 7000).
    -c        : Check plugins only with CVE associated.
    -R file   : Reload plugin list. Use -n option to control the size (This take several minutes)
    -o file   : Output file. (Default "output.txt")
    -i file   : Input plugin list. (Need to start the program)
    -s time   : Min sleep time between two probes. Time in seconds. (Default 10)
    -M time   : Max sleep time between two probes. Time in seconds. (Default 20)
    -t num    : Number of threads. (Default 1)
    -h        : Display help. (More info: http://iniqua.com/labs/) 

Examples:

  * Reload first 5 plugins list:
    	plecost -R plugins.txt -n 5
  * Search vulnerable sites for first 5 plugins:
        plecost -n 5 -G -i plugins.txt
  * Search plugins with 20 threads, sleep time between 12 and 30 seconds for www.example.com:
        plecost -i plugin_list.txt -s 12 -M 30 -t 20 -o results.txt www.example.com        


```

Example Usage
-------

Links
-------

