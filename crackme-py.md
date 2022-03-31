# Crackme-py

This challenge simply provides a python file 'crackme.py'

This file has two functions. One is a ROT47 decoder, with the helpful hint that decode and encode are the same for ROT47. The other function simply compares two given user input numbers and return which is larger.

There is also an encoded string 'bezos_cc_secret' I wonder what method of encoding it uses....

## Solution

The ROT47 function is not called in the original file. Copying the original file to 'cracker.py', removing the useless function call, and calling the ROT47 function on 'bezos_cc_secret' returns:

```
picoCTF{1|\/|_4_p34|\|ut_a79b6c2d}
```