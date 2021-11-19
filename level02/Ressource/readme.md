##LEVEL02

```
    level02@SnowCrash:~$ ls
    level02.pcap
    scp -P 4242 level02@10.11.100.161:/home/user/level02/level02.pcap .
    password:f2av5il02puano7naaf6adaaf
```

now that we have "level02.pcap" in our local machine "i'm using MACOS", we can use wireshark to get more info on this record.

```
    in Frame 20 the server send this data to the user:

0000   0d 0a 4c 69 6e 75 78 20 32 2e 36 2e 33 38 2d 38   ..Linux 2.6.38-8
0010   2d 67 65 6e 65 72 69 63 2d 70 61 65 20 28 3a 3a   -generic-pae (::
0020   66 66 66 66 3a 31 30 2e 31 2e 31 2e 32 29 20 28   ffff:10.1.1.2) (
0030   70 74 73 2f 31 30 29 0d 0a 0a 01 00 77 77 77 62   pts/10).....wwwb
0040   75 67 73 20 6c 6f 67 69 6e 3a 20                  ugs login: 

```
then the user send data in each frame
```
Frame       Data
22          0000   6c                                                l
25          0000   65                                                e
28          0000   76                                                v
31          0000   65                                                e
34          0000   6c                                                l
37          0000   58                                                X
40          0000   0d                                                .
```
hex "0d" stand for CR (carriage Return) "i assume its entre in this casse"

after that in fram 43 the server ask for password 
```
Frame       Data
43          0000   00 0d 0a 50 61 73 73 77 6f 72 64 3a 20            ...Password: 
```
then the user send this data

```
Frame       Data
45          0000   66                                                f
47          0000   74                                                t
49          0000   5f                                                _
51          0000   77                                                w
53          0000   61                                                a
55          0000   6e                                                n
57          0000   64                                                d
59          0000   72                                                r
61          0000   7f                                                .
63          0000   7f                                                .
65          0000   7f                                                .
67          0000   4e                                                N
69          0000   44                                                D
71          0000   52                                                R
73          0000   65                                                e
75          0000   6c                                                l
77          0000   7f                                                .
79          0000   4c                                                L
81          0000   30                                                0
83          0000   4c                                                L
85          0000   0d                                                .
```

7f in ascii stand for DEL

so our password is "ft_waNDReL0L"

```
    su flag02
    password: ft_waNDReL0L
```
```
    getflag
```
result: **kooda2puivaav1idi4f57q8iq**