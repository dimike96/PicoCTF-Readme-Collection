# 2Warm

This challenge asked to convers the decimal number `42` into binary, or base 2.  

## Solution

I wrote a quick python function to do the conversion.

```python
def main():
    base10_val = input('base10here')
    binary = bin(base10_val).replace('0b', '')
    print("picoCTF{" + str(binary) + "}")
```

Something like that was my idea. (Check `dec-to-bin.py` to see final execution.)

The flag I got was:

```
picoCTF{101010}
```