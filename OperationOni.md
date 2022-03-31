# Operation Oni

In this challenge we're given a disk image and need to get its SSH key so we can log into it and get our flag

## Solution

Some of the other challenges provided an introductiont to Sleuthkit and this is a good opportunity to utilize Autopsy to extract information from an disk image.

I got autopsy loaded and set up a new case for this challenge. Here

In autopsy we can go into file analysis and see directory structures for given volumes

Volume 3 was the main filesystem we needed to look into

Knowing we're looking for an SSH key we might initially go to /etc/ssh and take a peek at ssh_config / sshd_config to get an idea how SSH is configured

This wasn't really useful but I extracted the information regardless and moved on to check the /.ssh directory

Here we can find the id_25519 private and public keys we need. If we extract the private key we can run the following to remote in and get our flag:

```
chmod 400 /path/to/private/key 
ssh -i /path/to/private/key -p 51635 ctf-player@saturn.picoctf.net
```

This gets us in, then we can simply run ```ls``` and see a flag.txt

Run ```cat flag.txt```

And we have our flag!

```
picoCTF{k3y_5l3u7h_d6e19567}
```