# Big Zip

This challenge provides a zip file from which to extract a flag. 
The gimmick here lies in the obtuse structure of the zip file made up of many incoherently named subdirectories and files.

## Solution

We can use `grep` recursively to operate on an entire directory.

1. Extract the zip file using your method of choice. I used `binwalk -e big-zip-files.zip`
2. Grep for our flag identifier recursively with something like `grep -rni "pico"` from the parent directory.

We use the `-r` flag to make grep recursive, the `-n` flag shows us what line any match is on within its file (not so important here but useful in other situations), and the `-i` flag to run a case-insensitive match.

We should get some result like this:
```
λ grep -rni "pico"
_big-zip-files.zip.extracted/big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:1:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
flag.txt:1:picoCTF{gr3p_15_m4g1c_ef8790dc}
```

Our flag is then:
```
picoCTF{gr3p_15_m4g1c_ef8790dc}
```
