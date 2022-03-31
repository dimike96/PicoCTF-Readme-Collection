# Matryoshka Doll

Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one?

The challenge provided an image of a matryoshka doll

## Solution

To check for hidden files inside the image as implied by the challenge we can run:

```
binwalk -e dolls.jpg
```

We have to do that for a few more layers until we get a flag.txt file.

```
picoCTF{bf6acf878dcbd752f4721e41b1b1b66b}
```


