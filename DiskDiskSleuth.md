# Disk, Disk, Sleuth!

This challenge provides a gzipped disk image for us to try and retrieve the flag from.

## Solution

We can unzip the image by running ```gunzip``` on the original file.

The first real move would be to try running ```strings``` on the file.

If we do we see a massive output. Thankfully we can use the powerful tool ```grep``` to help dig through it.

Let's try a classic:

```bash
strings dds1-alpine.flag.img | grep "picoCTF"
```

Right away this will get us the flag!

In my ```getflag.sh``` file I added an extra step that filtered out the extra stuff that grep returns using python as one way to make a clean ```flag.txt```.

```
picoCTF{f0r3ns1c4t0r_n30phyt3_564ff1a0}
```