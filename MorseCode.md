# Morse Code

As you may expect from the title this challenge was about turning a .wav file with morse code into a proper flag

## Solution

I'm sure there are many ways to decode morse. The simplest for me was to search online for a web based tool where I could upload a sample and get the output text.

The tool I used can be found here: https://morsecode.world/international/decoder/audio-decoder-adaptive.html

This gave me the string ```WH47 H47H 90D W20U9H7```

From here we just need to properly format it, and the challenge text says to use lowercase

We can do that manually or use something like this in python:

```
flag_content = "WH47 H47H 90D W20U9H7"

flag_content = flag_content.lower()
flag_content = flag_content.replace(' ','_')

flag = "picoCTF{" + flag_content + "}"

print(flag)
```

Giving us a nice flag to submit!

```
picoCTF{wh47_h47h_90d_w20u9h7}
```


