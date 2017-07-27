# TWCracker

____
Any pentester that has spent enough time in TWC/Spectrum service areas has most likely come across dozens of networks with names like TG852G22 or TC8715D3E, or some other {router model}xx name. Most, if not all, of these networks are just lazy default configurations that can be *very* easily cracked. You really don't even need a program to do it for you (buy why not, right?).

Basically, Time Warner / Spectrum sets up (many) default networks like so:

    ESSID:  TG852G01
    BSSID: DE:AD:BE:EF:CA:FE
    PSK:   TG852GEFCA01

If it's not immediately obvious by looking at it, allow me to break it down:

- Take the 4th and 5th sets of the BSSID (in our case, EF + CA)
- Split the last two characters off of the ESSID
- Concat the sets of the BSSID we just grabbed
- Concat the last two ESSID characters back onto the string
- Profit (?)

This is sort of a pain to do in the field, so I crafted this tiny ruby script to facilitate our laziness. 

    Usage: ./twcracker -b <BSSID> -e <ESSID>

The script automagically creates the password, prints it off, and then sends the ESSID + BSSID through wpa_passphrase and saves the configuration in <BSSID>.conf. From there, just use wpa_supplicant to authenticate (or just copy/paste the password). 

Enjoy. 


