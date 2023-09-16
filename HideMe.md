# HideMe

In this challenge we're given a suspicious `.png` file from which to extract a flag.

## Solution

Some of the first things we might be inclined to try when given an image file is to run `file`, `exiftool`, or the classic `strings`.

`file` doesn't return anything particularly interesting however in our trusty `strings` we see something that might catch our eye.

The last two lines of strings output:
```
secret/UT
secret/flag.pngUT
```

This might cause us to question if there is a "secret" directory in this file, and it is in fact an archive. Lets `binwalk` to see what we get.

`binwalk -e flag.txt` shows us there is indeed a secret directory, with an alternate flag.png file.

Now here if you are me, you will endlessly recurse with binwalk and exiftool and everything you can think of on the file instead of just.. opening it.

Otherwise you will open the file in an image viewer right away and see the flag clearly in the picture itself.

`picoCTF{gr3p_15_m4g1c_ef8790dc}`