# PW Crack 1

We are provided a python script that acts as a password checker, and an encrypted flag. Can we find the password to get the flag?

## Solution

Sometimes sensitive data is hardcoded into programs. In this one there was a line:
```
if( user_pw == "f014"):
```

Followed by decrypting and printing the flag :)

So password = f014 and flag was:
```
picoCTF{545h_r1ng1ng_6ed6f065}
```