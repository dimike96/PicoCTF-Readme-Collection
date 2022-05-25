# Disk, Disk, Sleuth 2!

Again we are given a gzipped disk image to retrieve a flag from. Here we're told the file is named "down-at-the-bottom.txt"

## Solution

Firstly, we can unzip using the ```gunzip``` command.

Nextly, we need to dig into file. These challenges heavily suggest sleuthkit but I used binwalk and it was pretty easy and quick!

If you run:
```
binwalk -e dds2-alpine.flag.img
```

You get an output directory with the filesystem!

Lets cd into the output directory.

From here we can use a find command piped to grep since we know the name of the file we are looking for:
```
find . -print | grep -i down
```

This shows us the path to any file starting with 'down'. If there was too much noise we could always be more specific, but we can tell the path we want is:
```
./ext-root/root/down-at-the-bottom.txt
```

If we cat this file we can see that the flag is there, but it's somewhat obfuscated with extra spaces and characters to defeat or simple strings to grep we did in the last challenge. 

From here I coppied and moved this file to my working directory, named it "flag-encoded.txt" and wrote a quick bit of python to turn this into a clean flag.txt:

```python
#!/bin/python3

import re

with open('flag-encoded.txt') as encoded: 
    lines = encoded.readlines()

stage_1 = lines[2] + lines[6] + lines[10] # 2, 6, 10 are the lines with the actual flag content

stage_2 = re.sub('[(\s)]', '', stage_1) # Substitute the obfuscating character class with nothing

# print(stage_2)

with open("flag.txt", 'w') as decoded:
    decoded.write(stage_2)
    decoded.close()
```

This gives the flag!
```
picoCTF{f0r3ns1c4t0r_n0v1c3_db59daa5}
```