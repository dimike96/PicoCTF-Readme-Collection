# Glitch Cat

Our flag printing service has started glitching! ```nc saturn.picoctf.net 53933```

## Solution

If we run the netcal command we are greeted with a strange output:
```
'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'
```

The hints help push you in the right direction, but you might observe that this is proper python syntax!

We can exit the connection and run as a terminal one-liner:
```python
python3 -c 'print(\'picoCTF{gl17ch_m3_n07_\' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + \'}\')'
```

Python easily concatonates the flag using the ASCII values seen in the output.

```
picoCTF{gl17ch_m3_n07_a4392d2e}
```