## Moving The Ctrl Key
In the X Window System, you can swap Control and Caps Lock with the xkb option ctrl:swapcaps. If you don’t ever need Caps Lock you can instead of swapping the two set Caps Lock to be another Control. This is done with ctrl:nocaps. Use one of these from command line:

```bash
$ setxkbmap -option ctrl:swapcaps     # Swap Left Control and Caps Lock
$ setxkbmap -option ctrl:nocaps       # Make Caps Lock a Control ke<
```
