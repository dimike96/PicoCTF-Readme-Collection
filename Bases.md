# Bases

In this challenge we are given a string and asked to figure out what it means.

What we're given: ```bDNhcm5fdGgzX3IwcDM1```

## Solution

Based on the format and commonly used bases we can deduce that this string is encoded using base64.

In python we can then use the base64 module to decode it.

In my case I included the further bytes to string conversion, however you can get the flag without this step if you ignore the bytes padding. (b'flag')

```
import base64
output = ''.join(map(chr, base64.b64decode(provided_string)))
print(output)
```

This gives us the flag:
```
picoCTF{l3arn_th3_r0p35}
```
