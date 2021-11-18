#LEVEL01

to get information about flag01 user we can look in /etc/passwd

```
    cat /etc/flag01 | grep flag01
```
result :

flag01:**42hDRfypTqqnw**:3001:3001::/home/flag/flag01:/bin/bash
as we can see 42hDRfypTqqnw is the encrypted password 

and as stated in this [link](https://community.hpe.com/t5/HP-UX-General/decrypt-password-in-the-etc-password-file/m-p/3366207#M100091) if we go to the last question we can understand how this encryption work and how does softwares like jhon the ripper decrypte it.

so i did use a VM runing on centos8 to run jhon the ripper.

```
    ./john-1.9.0/run/john --show <(echo 42hDRfypTqqnw)
```
result:
```
    ?:abcdefg
```
now we can connect to flag01
```
    su flag01
    password: abcdefg
    getflag
```
result:
```
    f2av5il02puano7naaf6adaaf
```
```
    su level02
    password: f2av5il02puano7naaf6adaaf
```