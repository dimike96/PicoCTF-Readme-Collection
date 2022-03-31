# Basic Mod 1

In this challenge we're given an encrypted message and a scheme to decrypt it.

We're told to take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore.

## Solution

Basically we can just follow the directions in out programming language of choice.

Here is what I did in python:
```
import string
ALPHABET = string.ascii_uppercase
message = "202 137 390 235 114 369 198 110 350 396 390 383 225 258 38 291 75 324 401 142 288 397"
message_list = message.split(" ")
def decode_message(list):
    list_mod_37 = []
    converted_message = ""
    for element in list:
        element = int(element) % 37
        list_mod_37.append(element)
    for element in list_mod_37:
        if element < 26:
            element = ALPHABET[element]
            converted_message += element
        elif element < 36 and element > 25:
            element = str(element - 26)
            converted_message += element
        elif element == 36:
            element = "_"
            converted_message += element
    flag = "picoCTF{"
    return flag + converted_message + "}"
    return converted_message
print(decode_message(message_list))
```

This produces the flag:
```
picoCTF{R0UND_N_R0UND_B6B25531}
```