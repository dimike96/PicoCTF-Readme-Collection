# Basic Mod 2

This is another challenge using modular! We're given an encrypted message and the steps to solve it.

We're told to take each number mod 41 and find the modular inverse for the result. Then map to the following character set: 1-26 are the alphabet, 27-36 are the decimal digits, and 37 is an underscore.

## Solution


Essentially we just need to follow the steps. To make it easy we use our language of choice, in my case python.

The first step (finding the values mod 41) isn't too hard. Simply ```new_num = n % 41``` gets us there.

I did not know what was necessarily meant by the "modular inverse" and had to spend a fair amount of time reading up on it. 

I found this description helpful:
>The modular inverse of A mod C is the B value that makes A * B mod C = 1

And found a good python implementation:

```
y = pow(x, -1, p)
```
Where y is your modular inverse, x is your starting number, and p is your modulus.
>Source: https://stackoverflow.com/questions/4798654/modular-multiplicative-inverse-function-in-python

Here is my code:
```
import string
ALPHABET = " " + string.ascii_uppercase
message = "104 85 69 354 344 50 149 65 187 420 77 127 385 318 133 72 206 236 206 83 342 206 370"
message_list = message.split(" ")

def decode_message(list):
    list_mod_41 = []
    list_inv_mod = []
    converted_message = ""
    for element in list:    # This does the modular
        element = int(element) % 41
        list_mod_41.append(element)
    for element in list_mod_41:     # This does the modular inverse
        element = pow(element, -1, 41)
        list_inv_mod.append(element)
    for element in list_inv_mod:     # This starts the alphabet conversion section
        if element <= 26:
            element = ALPHABET[element]
            converted_message += element
        elif element < 37 and element > 26:
            element = str(element - 27)
            converted_message += element
        elif element == 37:
            element = "_"
            converted_message += element
    flag = "picoCTF{"
    return flag + converted_message + "}"

print(decode_message(message_list))
```

This got me the flag:
```
picoCTF{1NV3R53LY_H4RD_DADAACAA}
```
