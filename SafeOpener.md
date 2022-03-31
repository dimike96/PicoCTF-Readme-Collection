# Safe Opener

In this challenge we're given a Java file is supposedly to help someone  retrieve the key to their safe. If we get the password from it we can get our flag.

## Solution

If we start with simply taking a look at the Java file there are some things that might catch our eye

```
Base64.Encoder encoder = Base64.getEncoder();
String encodedkey = "";
String key = "";
```

```
String encodedkey = "cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz"
```

We can tell that the encoding method is base64 which we can easily decode

```
import base64

subject = "cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz"

print(base64.b64decode(subject))
```

This gives us the password ```pl3as3_l3t_m3_1nt0_th3_saf3```

So we have the flag!

```
picoCTF{pl3as3_l3t_m3_1nt0_th3_saf3}
```