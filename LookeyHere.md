# Lookey Here

This challenge gives us a very long text file for us to get the flag from

## Solution

A useful tool we could use is grep if we are working from the terminal 

If we run:

```
grep "picoCTF" anthem.flag.txt > out.txt
```

The out.txt file will have the line where it found a match to what we put in quotes from the file we specified imediately after

Out.txt / grep output:

```
      we think that the men of picoCTF{gr3p_15_@w3s0m3_58f5c024}
```

Flag:

```
picoCTF{gr3p_15_@w3s0m3_58f5c024}
```