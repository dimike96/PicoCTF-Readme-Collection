# Money-ware
In this challenge we are told about someone being a victim of ransomware and given a bitcoin address.
To get our flag we are tasked with finding the name of the ransomware in question.

## Solution
Since crypto is used extensively in malicious cyber activity there are various resources we can use to track and associate wallet addresses and threat actors.

If we simply google for crypto currency abuse databases we can find something like this:
https://www.chainabuse.com/address/1Mz7153HMuxXTuR2R1t78mGSdzaAtNbBWX

This site seems to have various submissions associated with our subject wallet address.
We scroll through several reports that simply associate it with ransomware generally before finding one that directly to a blog post about the "Petya" ransomware:
https://www.avira.com/en/blog/petya-strikes-back

Therefore we can safely say that the victim in our prompt was targetted by Petya, and our flag is `picoCTF{Petya}`
