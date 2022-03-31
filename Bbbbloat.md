# Bbbbloat

This is a binary exploitation challenge where we've been given a file ```bbbbloat.elf``` and need to manage to get out flag from it.

## Solution

This isn't my strongest subject but it's always fun to learn.

Let's run strings to get an initial idea what might happen when we run it:

```
strings bbbbloat.elf
```

For me the only thing of note I find with that are these strings:

```
What's my favorite number?
Sorry, that's not it!
```

If we run it with:

```
chmod +x bbbbloat.elf
./bbbbloat.elf
```

The program asks us for it's favorite number like we just saw. Popular guesses don't work, so we will dig deeper.

Lets try ghidra! I barely know anything about using it but you really don't have to for this challenge!

If we open ghidra and get a project going for our .elf file and just start looking around we might be able to spot that part of the program that asks about it's favorite number. (see the Screenshot.png)

```
printf("What\'s my favorite number? ");
_isoc99_scanf();
if (local_48 == 0x86187) {
    ((SOME CODE))
}
else {
    puts("Sorry, that\'s not it!")
}
```

So the favorite number is ```0x86187```! 

We might recognize this as hexadecimal and convert it using any number of tools and find the decimal equivalent to be ```549255```

Passing that to out program will result in getting the flag!

```
picoCTF{cu7_7h3_bl047_695036e3}
```






