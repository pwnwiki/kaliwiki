KSTATS

NAME
       kstats  -  show  statistical  FMS algorithm votes for an ivs dump and a
       specified WEP key

SYNOPSIS
       kstats <ivs file> <104-bit key>

DESCRIPTION
       kstats is a tool designed to show the FMS algorithm votes  for  an  ivs
       dump (intialization vectors) with a specified WEP key. The ivs dump can
       be get by using the combinaison of both airodump(1) and ivstools(1).

EXAMPLE
       kstats kstats out.ivs 123456789ABCDEF123456789AB