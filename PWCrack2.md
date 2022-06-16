# PW Crack 2

We are provided an encrypted flag file and a password checking python script

## Solution

Again sensitive information is in the script, this time encoded using the unicode representation of each character, converting each to their corresponding character and concatenating them to get the password.

```
if( user_pw == chr(0x62) + chr(0x37) + chr(0x30) + chr(0x37) ):
```

Simply we can run:
```
user_pw = chr(0x62) + chr(0x37) + chr(0x30) + chr(0x37)
print(user_pw)
```

This tells us the password is ```b707```

So we can get the flag:
```
picoCTF{tr45h_51ng1ng_f21caf8e}
```
