

```
    level09@SnowCrash:~$ ./level09 11111
    12345
    level09@SnowCrash:~$ cat token
    f4kmm6p|=�p�n��DB�Du{��
```

as we can see our executable shift charecters by its index on the string
and token has a non printable characters so it must've been shifted by level09
we will creat a script that reverse that
```
    #include <stdio.h>
    #include <stdlib.h>
    int main()
    {
    char ch, file_name[25];
    FILE *fp;

    printf("Enter name of a file you wish to see\n");
    gets(file_name);

    fp = fopen(file_name, "r"); // read mode

    if (fp == NULL)
    {
        perror("Error while opening the file.\n");
        exit(EXIT_FAILURE);
    }

    printf("The contents of %s file are:\n", file_name);

    int i = 0;
    while((ch = fgetc(fp)) != EOF)
        printf("%c", ch - i++);
    printf("\n");

    fclose(fp);
    return 0;
    }
```
```
    level09@SnowCrash:~$ gcc hexPrint.c 
    level09@SnowCrash:~$ ./a.out 
    Enter name of a file you wish to see
    token
    The contents of token file are:
    f3iji1ju5yuevaus41q1afiuq
```


```
flag09@SnowCrash:~$ getflag
Check flag.Here is your token : s5cAJpM8ev6XHw998pRWG728z
level09@SnowCrash:~$ su level10
Password:s5cAJpM8ev6XHw998pRWG728z
level10@SnowCrash:~$ 
```