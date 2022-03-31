# Warmed Up

What is 0x3D (base 16) in decimal (base 10)?

picoCTF{my_answer_goes_here}

## Solution

I have a python program called MultiTool.py (https://www.github.com/dimike96/MultiTool) which has various encoding and decoding functions. Passing `3D` to it's hex decoding function yielded: `=`

The challenge however needs an additional conversion to decimal (base 10).

Googling ASCII to Decimal for `=` yielded `61`. (Will also include `ascii_b10.py` that can do that too)

The flag would therefore be:
```
picoCTF{61}
```