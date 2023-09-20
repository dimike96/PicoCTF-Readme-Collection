# PcapPoisoning

In this challenge we're given a `.pcap` packet capture file to analyze and find our flag. We

## Solution

When dealing with pcap files my first move is usually to open them in wireshark and scroll through to get an idea of what we're dealing with.

We initially see a long bunch of FTP packets before we find a bunch of TCP packets.

I find that in challenges like these these sorts of transitions can be points of interest. So lets look at the first TCP packet here, in this case packet 507:
```
0000   45 00 00 52 00 01 00 00 40 06 c3 90 ac 10 00 02   E..R....@.......
0010   0a fd 00 06 00 14 00 15 00 00 00 00 00 00 00 00   ................
0020   50 02 20 00 48 4e 00 00 70 69 63 6f 43 54 46 7b   P. .HN..picoCTF{
0030   50 36 34 50 5f 34 4e 34 4c 37 53 31 53 5f 53 55   P64P_4N4L7S1S_SU
0040   35 35 33 35 35 46 55 4c 5f 30 66 32 64 37 64 63   55355FUL_0f2d7dc
0050   39 7d                                             9}
```

We can see our flag is `picoCTF{P64P_4N4L7S1S_SU55355FUL_0f2d7dc9}`!