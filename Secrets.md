# Secrets

In this challenge we're given a website(```http://saturn.picoctf.net:50167/```), told that secret info is on one of it's pages, and set loose.

## Solution

Utilizing our browsers developer tools we can view the sources of the pages we can see, as their front facing content is bland and uninteresting.

What stuck out to me from the homepage:
```
<link href="secret/assets/index.css" rel="stylesheet" />
```

Reference to a "secret" folder... Let's see what happens if we try to go directly there.

A meme. And a hint we are on the right track! 

Viewing the source here we see:
```
<link rel="stylesheet" href="hidden/file.css" />
```

Referencing a "hidden" folder. Again we will go to that.

This time we land on a login page. But that's probably a distraction, again to the source!

```
<link href="superhidden/login.css" rel="stylesheet" />
```

Ahh a "superhidden" folder!

The page we find there:
```
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <link rel="stylesheet" href="mycss.css" />
  </head>

  <body>
    <h1>Finally. You found me. But can you see me</h1>
    <h3 class="flag">picoCTF{succ3ss_@h3n1c@10n_51b260fe}</h3>
  </body>
</html>
```

## Flag:
```
picoCTF{succ3ss_@h3n1c@10n_51b260fe}
```

