# rtl_fm

Notes
-------
a simple FM demodulator for RTL2832 based DVB-T receivers


Help Text
-------
```
rtl_fm, a simple narrow band FM demodulator for RTL2832 based DVB-T receivers

Use:	rtl_fm -f freq [-options] [filename]
	-f frequency_to_tune_to [Hz]
	 (use multiple -f for scanning, requires squelch)
	 (ranges supported, -f 118M:137M:25k)
	[-s sample_rate (default: 24k)]
	[-d device_index (default: 0)]
	[-g tuner_gain (default: automatic)]
	[-l squelch_level (default: 0/off)]
	[-o oversampling (default: 1, 4 recommended)]
	[-p ppm_error (default: 0)]
	[-E sets lower edge tuning (default: center)]
	[-N enables NBFM mode (default: on)]
	[-W enables WBFM mode (default: off)]
	 (-N -s 170k -o 4 -A fast -r 32k -l 0 -D)
	filename (a '-' dumps samples to stdout)
	 (omitting the filename also uses stdout)

Experimental options:
	[-r output_rate (default: same as -s)]
	[-t squelch_delay (default: 20)]
	 (+values will mute/scan, -values will exit)
	[-M enables AM mode (default: off)]
	[-L enables LSB mode (default: off)]
	[-U enables USB mode (default: off)]
	[-R enables raw mode (default: off, 2x16 bit output)]
	[-F enables high quality FIR (default: off/square)]
	[-D enables de-emphasis (default: off)]
	[-C enables DC blocking of output (default: off)]
	[-A std/fast/lut choose atan math (default: std)]

Produces signed 16 bit ints, use Sox or aplay to hear them.
	rtl_fm ... - | play -t raw -r 24k -e signed-integer -b 16 -c 1 -V1 -
	             | aplay -r 24k -f S16_LE -t raw -c 1
	  -s 22.5k - | multimon -t raw /dev/stdin


```

Example Usage
-------


```

```

Links
-------
[Author's guide](http://kmkeen.com/rtl-demod-guide/)

[rtl-fm Ubuntu Trusty manpage](http://manpages.ubuntu.com/manpages/trusty/man1/rtl_fm.1.html)
