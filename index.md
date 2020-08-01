
# Over-The-Wire-Bandit
Over The Wire Bandit wargames walkthrough
```
ssh -p 2220 bandit.labs.overthewire.org -l bandit0
```
level 0      boJ9jbbUNNfktd78OOpsqOltutMc3MY1

level 1
		cat /home/bandit1/-
		CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

level 2		cat spaces\ in\ this\ filename
		UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK

level 3
```
cd inhere/
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -las
total 12
4 drwxr-xr-x 2 root    root    4096 Oct 16  2018 .
4 drwxr-xr-x 3 root    root    4096 Oct 16  2018 ..
4 -rw-r----- 1 bandit4 bandit3   33 Oct 16  2018 .hidden
bandit3@bandit:~/inhere$ cat .hidden
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

level 4		
		```
		cat /home/bandit4/inhere/-file07
		koReBOKuIDDepwhWk7jZC0RTdopnAYKh
 		```

level 5		
		```
		ls -las
		bandit5@bandit:~/inhere/maybehere07$ cat .file2
		DXjZPULLxYr17uwoI01bNLQbtFemEgo7
		```

level 6
		```
		find /  -user bandit7 -group bandit6 -size 33c
		cat /var/lib/dpkg/info/bandit7.password
		HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
		```
		
level 7		cat data.txt |grep millionth
		millionth       cvX2JJa4CFALtqS87jk27qwqGhBM9plV
	
level 8		cat data.txt | sort |uniq -c --count 
		1 occurenece  UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

level 9		strings data.txt
		truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

level 10	base64  -d data.txt 
		The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

level 11	cat data.txt 
		Gur cnffjbeq vf 5Gr8L4qetPEsPk8htqjhRK8XSP6x2RHh
		
	python3
	Python 3.5.3 (default, Sep 27 2018, 17:25:39) 
	[GCC 6.3.0 20170516] on linux
	Type "help", "copyright", "credits" or "license" for more information.
	>>> import codecs
	>>> passwd = codecs.decode('Gur cnffjbeq vf 5Gr8L4qetPEsPk8htqjhRK8XSP6x2RHh','rot_13');
	>>> passwd
	'The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu'
	>>> 
---
	
level 12	after a lot of mv and gunziping,bunziping and tar
		The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL

level 13	ls
		ssh bandit14@localhost -i sshkey.private
		cat /etc/bandit_pass/bandit14
		4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e

level 14-15
```
nc localhost 30000
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr
```


level 15-16

openssl s_client -connect localhost:30001

    Start Time: 1586600296
    Timeout   : 7200 (sec)
    Verify return code: 18 (self signed certificate)
    Extended master secret: yes
---
BfMYroe26WYalil77FoDi9qh59eK5xNr                
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

closed

level 16-17
 nmap 127.0.0.1 -p 31000-32000
 ncat 127.0.0.1 --ssl 31790
 you will recieve a rsa key, copy it
 cd /temp
 nano abcd
 paste the key in abcd
 ssh wont work the permisions for the file are too open we have to change it to 700
 chmod 7000 abcd
 ssh bandit17@localhost -i abcd 

level 17-18

diff passwords.old passwords.new
kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd

level 18-19
since .bashrc file has been modified to kick us out when login using ssh
ssh bandit18@localhost "bash --noprofile"
paste the password
ls
cat readme
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x

level 19-20

./bandit20-do 

./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j

level 20 -> 21

run two terminals with bandit20 
in one terminal do
./suconnect 35000
in the other terminal do 
nc -lvnp 35000
type the level 20 password

	bandit20@bandit:~$ nc -lvnp 35000
	listening on [any] 35000 ...
	connect to [127.0.0.1] from (UNKNOWN) [127.0.0.1] 41790
	GbKksEFF4yrVs6il55v6gwY5aVje5f0j   <-level20 password
	gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr   <-new password level 21

level 21 -> 22

		
cd  /etc/cron.d
ls
	bandit21@bandit:/etc/cron.d$ cat cronjob_bandit22
	@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
	* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
so we have to check out this cronjob_bandit22.sh
cd ..
cd ..
cd usr/bin
ls |grep cron
cat cronjob_bandit22.sh
	#!/bin/bash
	chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
	cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv

this file ->  t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv


cd /tmp
cat t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI    <- yes thats the password for level 22 !

level 22 -> 23

cd  /etc/cron.d
ls
cat /usr/bin/cronjob_bandit23.sh
	
	#!/bin/bash
	myname=$(whoami)	
	mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

	echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

	cat /etc/bandit_pass/$myname > /tmp/$mytarget
	
In this script the myname variable uses whoami which will mean badnit22 but we want for bandit23, it turns out we cant write and execute our own script
so modifying and executing the script isnt an option but these scripts are run periodically so that means we need the file which contains the password for bandit23
the variable mytarget is the file but currently the mytarget variable is equal to bandit22's password file and we want for bandit23,
	
	echo I am user $myname | md5sum | cut -d ' ' -f 1
	replace $myname to bandit23
	echo I am user bandit23 | md5sum | cut -d ' ' -f 1
	8ca319486bfbbc3663ea0fbe81326349 <- this will be the file which contains the password for bandit23 so lets cat it out
	cat 8ca319486bfbbc3663ea0fbe81326349
	jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n <-- This is the password for bandit23 hurray we did it!
	


