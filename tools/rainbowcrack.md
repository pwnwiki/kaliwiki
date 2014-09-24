# rcrack (rainbowcrack)

Notes
-------
RainbowCrack is a general propose implementation of Philippe Oechslin's faster time-memory trade-off technique. It crack hashes with rainbow tables.

RainbowCrack uses time-memory tradeoff algorithm to crack hashes. It differs from brute force hash crackers.

A brute force hash cracker generate all possible plaintexts and compute the corresponding hashes on the fly, then compare the hashes with the hash to be cracked. Once a match is found, the plaintext is found. If all possible plaintexts are tested and no match is found, the plaintext is not found. With this type of hash cracking, all intermediate computation results are discarded.

A time-memory tradeoff hash cracker need a pre-computation stage, at the time all plaintext/hash pairs within the selected hash algorithm, charset, plaintext length are computed and results are stored in files called rainbow table. It is time consuming to do this kind of computation. But once the one time pre-computation is finished, hashes stored in the table can be cracked with much better performance than a brute force cracker.

In this project, we focus on the development of optimized time-memory tradeoff implementation. GPU acceleration is another key feature of RainbowCrack software. By offloading most runtime computation to NVIDIA/AMD GPU, overall hash cracking performance can be improved further.


Help Text
-------
```
RainbowCrack 1.5
Copyright 2003-2010 RainbowCrack Project. All rights reserved.
Official Website: http://project-rainbowcrack.com/

usage: rcrack rt_files [rt_files ...] -h hash
       rcrack rt_files [rt_files ...] -l hash_list_file
       rcrack rt_files [rt_files ...] -f pwdump_file
       rcrack rt_files [rt_files ...] -n pwdump_file
rt_files:               path to the rainbow table(s), wildchar(*, ?) supported
-h hash:                load single hash
-l hash_list_file:      load hashes from a file, each hash in a line
-f pwdump_file:         load lanmanager hashes from pwdump file
-n pwdump_file:         load ntlm hashes from pwdump file

hash algorithms implemented in alglib0.so:
    lm, plaintext_len limit: 0 - 7
    ntlm, plaintext_len limit: 0 - 15
    md5, plaintext_len limit: 0 - 15
    sha1, plaintext_len limit: 0 - 20
    mysqlsha1, plaintext_len limit: 0 - 20
    halflmchall, plaintext_len limit: 0 - 7
    ntlmchall, plaintext_len limit: 0 - 15
    oracle-SYSTEM, plaintext_len limit: 0 - 10
    md5-half, plaintext_len limit: 0 - 15

example: rcrack *.rt -h 5d41402abc4b2a76b9719d911017c592
         rcrack *.rt -l hash.txt

```

Example Usage
-------
TThe rcrack program lookup existing rainbow tables for the plaintext of user supplied hash.

Six similar programs are available:

|Program	|User Interface	|GPU Acceleration|
|rcrack	|Command Line||	
|rcrack_cuda	|Command Line	|NVIDIA CUDA|
|rcrack_cl	|Command Line	|AMD OpenCL|
|rcrack_gui	|GUI	||
|rcrack_cuda_gui	|GUI	NVIDIA CUDA|
|rcrack_cl_gui	|GUI	|AMD OpenCL|
Command line program is ideal for batch processing, and GUI program is easy to use.

Rainbow tables used by rcrack program must already be sorted with rtsort program, and optionally converted to .rtc file format with rt2rtc program.

Rainbow Table Lookup with rcrack/rcrack_cuda/rcrack_cl Program

*General Use*

Assume rainbow tables are in directory c:\rt.

To crack single hash:

```
rcrack/rcrack_cuda/rcrack_cl c:\rt\*.* -h fcea920f7412b5da7be0cf42b8c93759
```
To crack multiple hashes:

```
rcrack/rcrack_cuda/rcrack_cl c:\rt\*.* -l hash_list_file
```
In the example above, hash_list_file is a text file with each hash in one line.

To lookup rainbow tables in multiple directories:

```
rcrack/rcrack_cuda/rcrack_cl c:\rt1\*.* c:\rt2\*.* -l hash_list_file
```
In the example above, the rcrack/rcrack_cuda/rcrack_cl program will lookup rainbow tables in c:\rt1 and c:\rt2 directories sequentially.

*Special Consideration for LM/NTLM Hash*

LM/NTLM hashes are usually saved in text file of pwdump format.

Content of typical pwdump file:

```
Administrator:500:1c3a2b6d939a1021aad3b435b51404ee:e24106942bf38bcf57a6a4b29016eff6:::
Guest:501:a296c9e4267e9ba9aad3b435b51404ee:9d978dda95e5185bbeda9b3ae00f84b4:::
```
To load and crack LM hashes from pwdump file:

```
rcrack/rcrack_cuda/rcrack_cl c:\rt\*.* -f pwdump_file
```
To load and crack NTLM hashes from pwdump file:

```
rcrack/rcrack_cuda/rcrack_cl c:\rt\*.* -n pwdump_file
```

*Rainbow Table Generation*

The rtgen program generate rainbow tables based on parameters specified by user, and the rtsort program post processing the rainbow tables to enable fast lookup.

After the two steps above (rtgen and rtsort), rainbow tables can be used to crack hashes with rcrack program.

*Generate Rainbow Table with rtgen Program*

Command line syntax of rtgen program:

```
rtgen hash_algorithm charset plaintext_len_min plaintext_len_max table_index chain_len chain_num part_index
```
An example to generate a rainbow table set with 6 rainbow tables:

```
rtgen md5 loweralpha-numeric 1 7 0 3800 33554432 0
rtgen md5 loweralpha-numeric 1 7 1 3800 33554432 0
rtgen md5 loweralpha-numeric 1 7 2 3800 33554432 0
rtgen md5 loweralpha-numeric 1 7 3 3800 33554432 0
rtgen md5 loweralpha-numeric 1 7 4 3800 33554432 0
rtgen md5 loweralpha-numeric 1 7 5 3800 33554432 0
```
Options:

|hash_algorithm	|Rainbow table is hash algorithm specific. Rainbow table for a certain hash algorithm only helps to crack hashes of that type.|
The rtgen program natively support lots of hash algorithms like lm, ntlm, md5, sha1, mysqlsha1, halflmchall, ntlmchall, oracle-SYSTEM and md5-half.
In the example above, we generate md5 rainbow tables that speed up cracking of md5 hashes.|
|charset	|The charset includes all possible characters for the plaintext.
"loweralpha-numeric" stands for "abcdefghijklmnopqrstuvwxyz0123456789", which is defined in configuration file charset.txt.
|plaintext_len_min
plaintext_len_max|
These two parameters limit the plaintext length range of the rainbow table.
In the example above, the plaintext length range is 1 to 7. So plaintexts like "a" and "abcdefg" are likely contained in the rainbow table generated. But plaintext "abcdefgh" with length 8 will not be contained.|
|table_index1	|The table_index parameter selects the reduction function.
Rainbow table with different table_index parameter uses different reduction function.|
|chain_len1	|This is the rainbow chain length. Longer rainbow chain stores more plaintexts and requires longer time to generate.|
|chain_num1	|Number of rainbow chains to generate.
Rainbow table is simply an array of rainbow chains. Size of each rainbow chain is 16 bytes.|
part_index	|To store a large rainbow table in many smaller files, use different number in this parameter for each part and keep all other parameters identical.|

There are many rainbow table characteristics determined implicitly by table generation parameters:

|Table Size	|With .rt rainbow table format, file size of a rainbow table equals to chain_num parameter multiplied by 16.|
|Key Space	|Key space is the number of possible plaintexts, calculated based on number of characters in charset and plaintext length range parameters.
In the example above, key space is 361 + 362 + 363 + 364 + 365 + 366 + 367 = 80603140212|
|Success Rate	|The time-memory tradeoff algorithm is a probabilistic algorithm.
Whatever the parameters are selected, there always exist many plaintexts (within the selected charset and plaintext length range) missing from the rainbow table generated.
In the example above, success rate is 99.9% with all 6 rainbow tables.
Success rate is determined by all table generation parameters except the hash_algorithm parameter.|

To start generating the first rainbow table, run following command in a command window:

```
rtgen md5 loweralpha-numeric 1 7 0 3800 33554432 0
```
CPU will be busy computing rainbow chains. On system with multi-core processor, all cores are fully utilized.

To pause table generation, just press Ctrl+C and rtgen program will exit. Next time if the rtgen program is executed with exactly same parameters, table generation is resumed.

This command takes hours to complete with ordinary processor.

When finished, a file "`md5_loweralpha-numeric#1-7_0_3800x33554432_0.rt`" sized 512 MB is in current directory. The file name stores all table generation parameters.

Now generate the remaining 5 rainbow tables:

```
rtgen md5 loweralpha-numeric 1 7 1 3800 33554432 0
rtgen md5 loweralpha-numeric 1 7 2 3800 33554432 0
rtgen md5 loweralpha-numeric 1 7 3 3800 33554432 0
rtgen md5 loweralpha-numeric 1 7 4 3800 33554432 0
rtgen md5 loweralpha-numeric 1 7 5 3800 33554432 0
```
Finally, there are 6 rainbow tables generated:

```
536,870,912 md5_loweralpha-numeric#1-7_0_3800x33554432_0.rt
536,870,912 md5_loweralpha-numeric#1-7_1_3800x33554432_0.rt
536,870,912 md5_loweralpha-numeric#1-7_2_3800x33554432_0.rt
536,870,912 md5_loweralpha-numeric#1-7_3_3800x33554432_0.rt
536,870,912 md5_loweralpha-numeric#1-7_4_3800x33554432_0.rt
536,870,912 md5_loweralpha-numeric#1-7_5_3800x33554432_0.rt
```
Sort Rainbow Table with rtsort Program

Rainbow table is an array of rainbow chains. Each rainbow chain has a start point and an end point. The rtsort program sorts the rainbow chains by end point to make binary search possible.

Run following command to sort all .rt rainbow tables in current directory:

```
rtsort *.rt
```
Never interrupt the rtsort program; otherwise the rainbow table being sorted may be damaged.

If free memory size is smaller than the size of rainbow table being sorted, temporary hard disk space as large as the rainbow table size is needed to store intermediate results.



Links
-------
* [rainbowcrack](http://project-rainbowcrack.com/)
* [rainbow tables](http://project-rainbowcrack.com/table.htm)