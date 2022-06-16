# Tab Tab Attack

This challenge provided an archive file "Addadshashanammu.zip"

## Solution

By viewing the contents of the archive using Ark we can see that the file contains a series of nested folders. Getting to the bottom of this tree there is an executable file 'fang-of-haynekhtnamet'.

Now run:

```
strings fang-of-hessenkhtnamet | grep pico
```
To get the flag: 

```
picoCTF{l3v3l_up!_t4k3_4_r35t!_a00cae70}
```
