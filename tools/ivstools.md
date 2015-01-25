IVSTOOLS

NAME
       ivstools  -  extract  IVs from a pcap file or merges several .ivs files
       into one

SYNOPSIS
       ivstools --convert <pcap file> <ivs output file> ivstools --merge  <ivs
       file 1> <ivs file 2> .. <output file>

DESCRIPTION
       ivstools  is  a  tool  designed to extract ivs (initialization vectors)
       from a pcap dump to an ivs file and it can also merge several ivs (ini‐
       tialization vectors) files into one..

EXAMPLE
       ivstools  --convert  wep_dump.cap  out.ivs  ivstools --merge myivs1.ivs
       myivs2.ivs myivs3.ivs allivs.ivs