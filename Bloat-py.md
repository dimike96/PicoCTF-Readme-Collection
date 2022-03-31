# Bloat.py

In this challenge we're given an encoved flag and a python script to decode it

## Solution

If we open up the script we can see a whole lot of obfuscation. However it's pretty simple.

We have a long alphabet string at the beginning of the script and the obfuscated strings are formed simply by indexing that string.

We can pull out any of these obfuscated strings into out own program with the alphabet and read them. If we trace through the program first we can learn that arg432 is going to give us the password.

My python:
```
import sys
a = "!\"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ"+ \
            "[\\]^_`abcdefghijklmnopqrstuvwxyz{|}~ "

arg432 = a[71]+a[64]+a[79]+a[79]+a[88]+a[66]+a[71]+a[64]+a[77]+a[66]+a[68]

print(arg432)
```

Which prints us the password as ```happychance```

Running the original script and passing this password to it gets us out flag!

```
picoCTF{d30bfu5c4710n_f7w_161a4f09}
```
