# Credstuff

This challenge gives us a user credential leak and wants us to get the flag from a specific users password

## Solution

What we get to work with is an archive containing a username list and an password list

We're told that they line up with each other, ie. line 1 on each list go together

We are also told our target user is ```cultiris```

If we find them on the username list we see they are in line 378

That line of the password list gives us:

```
cvpbPGS{P7e1S_54I35_71Z3}
```

We can tell this is encoded and the challenge hints that the other passwords might help us figure out how to decode

Just by looking we can tell the password is in our flag format, but also tell that the 'p' and 'C' from the flag prefix are swapped which might get us thinking about some kind of ROT cypher

If we skim the passwords like the int reccomends we could also see on line 204:

```
pICo7rYpiCoU51N6PicOr0t13
```

This gives us a good confirmation to try and reverse a ROT13 cypher to get our flag

Thrown together python:

```
username = "cultiris"
password = "cvpbPGS{P7e1S_54I35_71Z3}"

alpha = "abcdefghijklmnopqrstuvwxyz"
cap_alpha = alpha.upper()
cypher_alpha = "nopqrstuvwxyzabcdefghijklm"
digits = "0123456789"


print(cypher_alpha.index("a"))

def decode(pwd):
    decoded = ""
    for char in pwd:
        if char in digits:
            decoded += char
        elif char in alpha:
            char_pos = alpha.index(char)
            new_pos = char_pos + 13
            if new_pos > len(alpha):
                char = alpha[new_pos - len(alpha)]
            else:
                char = alpha[new_pos]
            decoded += char
        elif char in cap_alpha:
            char_pos = cap_alpha.index(char)
            new_pos = char_pos + 13
            if new_pos > len(cap_alpha):
                char = cap_alpha[new_pos - len(cap_alpha)]
            else:
                char = cap_alpha[new_pos]
            decoded += char
        else:
            decoded += char
    return decoded

print(decode(password)
```

Giving us a flag!

```
picoCTF{C7r1F_54V35_71M3}
```




