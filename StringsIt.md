# Strings It

This challenge provided a file named "strings" and asks for the flag to be found without opening it.

## Solution

Fairly straightforward given the name:
```
strings strings > output.txt
```

Then pull just the flag:
```
grep "picoCTF" output.txt > flag.txt
```

Returning:
```
picoCTF{5tRIng5_1T_827aee91}
```
