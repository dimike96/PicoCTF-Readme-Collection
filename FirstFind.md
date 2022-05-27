# First Find

In this challenge we're given a zip file and asked to find the file 'uber-secret.txt' within it.

## Solution

Pretty obviously we can expect using ```find``` is the best way to solve this.

The zip file is pretty crowded so lets try that.

```bash
>>> find . -print | grep -i uber

>>> ./files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
```

Now we just cat that file, and we can just copy the path from our previous command like so:
```bash
cat ./files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
```

And just like that we have out flag!
```
picoCTF{f1nd_15_f457_ab443fd1}
```