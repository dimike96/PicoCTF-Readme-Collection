# Mini RSA

This challenge focuses on decoding a weak RSA encoded message.  

The weakness mainly lies in the use of a small value for ```e```

## Solution

My first attempt was to use RsaCtfTool (https://github.com/Ganapati/RsaCtfTool)  

However I didn't find this successful.

Using code found here: https://github.com/Dvd848/CTFs/blob/master/2021_picoCTF/Mini_RSA.md was much more fruitful.

I'm still not fully understanding of the details of RSA so this is a fun example to push towards more understanding.

## Flag

```
picoCTF{e_sh0u1d_b3_lArg3r_7adb35b1}
```