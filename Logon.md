# Logon

This challenge was simply to log into a web portal as the user "Joe"

## Solutiuon

Tryin various logins, and based on the given hint we see that the only password check happens for the "Joe" user.

If we login in as anything and check the cookies we see three:
- admin
- username
- password

I initially tried changing the username to "Joe" but that didnt do anything so obviously next we try the admin cookie.

Setting it from "False" to "True" gives the flag!

```
picoCTF{th3_c0nsp1r4cy_l1v3s_d1c24fef}
```
