# File Types

In this challenge we're given a pdf, and told that it doesnt work right in someones pdf reader.

## Solution

First if we try to open the pdf normally we can plainly see some shell code!

Lets run ```cp flag.pdf flag.sh``` followed by ```chmod +x flag.sh``` and ```./flag.sh```

This produces a "flag" file. But it wasn't that easy...

Now let's run ```binwalk flag -e``` and cd to the extracted directory

It looks like we have a nesting dolls situation. If we:
```
binwalk -e 64
cd _64.extracted
lzip -d flag
binwalk flag.out
cp flag.out flag.lz4
lz4 -d flag.lz4
binwalk flag
cp flag flag.lzma
lzma -d flag.lzma
binwalk -e flag
cd _flag.extracted
binwalk 0
lzip -d 0
binwalk -e 0.out
cd _0.out.extracted
```
This gives us a "0" file we can run ```cat 0``` which just gives us hex:
```7069636f4354467b66316c656e406d335f6d406e3170756c407431306e5f6630725f3062326375723137795f37396230316332367d0a```

Let'r run:
```
echo -our-hex-goes-here | xxd -r -p
```

And finally we get our genuine flag!

```picoCTF{f1len@m3_m@n1pul@t10n_f0r_0b2cur17y_79b01c26}```

**Big thanks** to the author of this write up: https://hackmd.io/@jianting/H1IOdYfm5

I had no idea about the specific lzma and lz4 commands which had me stuck
