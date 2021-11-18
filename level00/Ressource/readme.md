#LEVEL00

in the video there is a hint in the readme file. it state that you need to find  files that can run under flag00 user;

```
    ls -l $(find / -user flag00 2>/dev/null)
```
it will display

----r--r-- 1 flag00 flag00 15 Mar  5  2016 /rofs/usr/sbin/john
----r--r-- 1 flag00 flag00 15 Mar  5  2016 /usr/sbin/john

so we can see whats inside **/usr/sbin/john**

```
    cat /usr/sbin/john
    or
    cat /rofs/usr/sbin/john
```
result:
```
    cdiiddwpgswtgt
```
we still can't log to flag00 using this password, so it's encrypted password.

if we use https://www.dcode.fr/identification-chiffrement

it will show us that this code can be decrypted in multiple ways.
we will use the first one [Déchiffrement Affine](https://fr.wikipedia.org/wiki/Chiffre_affine).

and the result for **cdiiddwpgswtgt** for the key (1,15):

```
    nottoohardhere
```

lets log to flag00 user 

```
    su flag00
    password: nottoohardhere
```

now we can get password for next level01

```
    getflag
```
result :
```
    Check flag.Here is your token : x24ti5gi3x0ol2eh4esiuxias
```
```
    su level01
    password: x24ti5gi3x0ol2eh4esiuxias
```