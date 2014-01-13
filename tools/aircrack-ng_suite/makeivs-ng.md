MAKEIVS-NG

NAME
       makeivs - generate a dummy IVS dump file with a specific WEP key

SYNOPSIS
       makeivs <ivs file> <104-bit key>

DESCRIPTION
       makeivs is a tool designed to generate an IVS dump file with an inputed
       WEP key.  The aim of is tools is to provide a way to create dumps  with
       a known encryption key for tests.

EXAMPLE
       makeivs makeivs out.ivs 123456789ABCDEF123456789AB