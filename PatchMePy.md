# Patchme.py 

This challenge gives us a python script and an encoded flag file.

## Solution

All we need to do is change the line in the script where it checks the user input against the correct password.

So in the line that compares the password to what it should be, we define what it should be ourselves! In my case I make it "lol":

```python
if user_pw == "lol":
```

*Note: You could easily just run the lines that decrypt and print directly:*

```python
decryption = str_xor(flag_enc.decode(), "utilitarian")
print(decryption)
```

Either methods will get you a nice flag!

```
picoCTF{p47ch1ng_l1f3_h4ck_f01eabfa}
```
