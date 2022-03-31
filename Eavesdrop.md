# Eavesdrop

In this challenge we're given a pcap file to dig through for our flag.

The only hiny we're given is that we know there was a conversation and a file transfer.

## Solution

Since we're given a pcap file we'll open it up in WireShark

Once there we can start looking through the packets

We might be incline to go into the analyze menu, and follow the tcp stream.

When I first did this I just scrolled my way through from beginning to end but know this might not always scale well if the capture was very large.

We can pick out a conversation where one person asks the other how to open some file.

The response will be important:

```
openssl des3 -d -salt -in file.des3 -out file.txt -k supersecretpassword123
```

Then they ask for the file to be resent which is great for us.

What we see for the file transfer in encrypted, but thanks to that message earlier we will be able to read it.

If we copy the data from the transfer packet as a hexstream we can convert it to the binary .des3 specified in the decryption command.

```
xxd -r -p /path/to/hexstream/txt file.des3
```

Next we'd just run the command from before, but if your experience is like mine this will produce a bad decrypt error :(

This had me stuck for a while until this write-up (https://ctftime.org/writeup/32854)

Basically theres something going on between the openssl version 1.1.1f that the picoCTF web-shell is using and the 1.1.1n that I have, and whatever some other people have.

If we take our hexstream and, from the web-shell run:
```
nano input.txt
```

Paste our hexstream in there, then:
```
xxd -r -p input.txt file.des3
```

And finally just run that decryption command:
```
openssl des3 -d -salt -in file.des3 -out file.txt -k supersecretpassword123
```

This gets our flag!

```
picoCTF{nc_73115_411_dd54ab67}
```