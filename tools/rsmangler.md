# rsmangler

Notes
-------
RSMangler will take a wordlist and perform various manipulations on it similar to those done by John the Ripper the main difference being that it will first take the input words and generate all permutations and the acronym of the words (in order they appear in the file) before it applies the rest of the mangles, for example given the following three input words:

* freds
* national
* bank

RSMangler would generate the following initial word list:

* freds
* national
* bank
* fredsnational
* fredsbank
* nationalfreds
* nationalbank
* bankfreds
* banknational
* fredsnationalbank
* fredsbanknational
* nationalfredsbank
* nationalbankfreds
* bankfredsnational
* banknationalfreds
* fnb

Each of these new words is then subject to the other mangles, because of this we strongly recommend with permutations mode enabled (default) you use a very small wordlist, 3 start words create a final list containing 4245 words and 5 start words creates a list containing 91975. As a test we tried it with a few hundred words and gave up when the output file got to 3G.

If you try to use a file with more than 5 words you will get a warning and the option to abort.

Other mangles include adding the numbers 1 to 123 to the start and end, 01 to 09 to the start and end, various case manipulations, leet speak, word reversal, ed and ing on the end and doubling words up.

The initial wordlist can either be specified as a file or can be piped in through STDIN.


Help Text
-------
```
rsmangler v 1.4 Robin Wood (robin@digininja.org) <www.randomstorm.com>

To pass the initial words in on standard in do:

cat wordlist.txt | ./rsmangler.rb --file - > new_wordlist.rb

All options are ON by default, these parameters turn them OFF

Usage: rsmangler.rb [OPTION]
	--help, -h: show help
	--file, -f: the input file, use - for STDIN
	--max, -x: maximum word length
	--min, -m: minimum word length
	--perms, -p: permutate all the words
	--double, -d: double each word
	--reverse, -r: reverser the word
	--leet, -t: l33t speak the word
	--full-leet, -T: all posibilities l33t
	--capital, -c: capitalise the word
	--upper, -u: uppercase the word
	--lower, -l: lowercase the word
	--swap, -s: swap the case of the word
	--ed, -e: add ed to the end of the word
	--ing, -i: add ing to the end of the word
	--punctuation: add common punctuation to the end of the word
	--years, -y: add all years from 1990 to current year to start and end
	--acronym, -a: create an acronym based on all the words entered in order and add to word list
	--common, -C: add the following words to start and end: admin, sys, pw, pwd
	--pna: add 01 - 09 to the end of the word
	--pnb: add 01 - 09 to the beginning of the word
	--na: add 1 - 123 to the end of the word
	--nb: add 1 - 123 to the beginning of the word
	--force - don't check ooutput size
	--space - add spaces between words

```

Example Usage
-------
Any helpful examples found around the web or from personal experience

```
Actual commands can go here
```

Links
-------
* [digininja](http://digi.ninja/projects/rsmangler.php)
* [randomstorm](https://www.randomstorm.com/resources/free-tools/rsmangler/)
