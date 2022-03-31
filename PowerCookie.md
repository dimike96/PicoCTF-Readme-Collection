# Power Cookie

Basic challenge where we're given a website (```http://saturn.picoctf.net:52021/```) and asked to find the flag!

## Solution

Simple introduction to cookie manipulation.

Using developer tools in the browser, under "Application" we can see the cookies the site uses. Theres one called "isAdmin" that seems useful, and is currently set to '0'.

We can try to change it in the dev tools, but I can't get them to save that way. Instead we can use an extension called "Cookie Editor" that has a decent UI for this.

Simply change "isAdmin" to '1' to get the flag!

## Flag

```
picoCTF{gr4d3_A_c00k13_65fd1e1a}
```