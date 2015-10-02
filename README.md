Name: M. Imshan

######Level0:
```
ssh to bandit0@bandit.labs.overthewire.org link using the password bandit0.

# ssh bandit0@bandit.labs.overthewire.org
```

######Level0->Level1:
```
Readme file is in our home directory. Simply “cat” it and grab the password for level1.

bandit0@melinda:~$ ls
readme
bandit0@melinda:~$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```

######Level1->Level2:
```
Password is in a file called “-“. We need to delimit the dash to read the file.

bandit1@melinda:~$ ls
-
bandit1@melinda:~$ cat ./-
V1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```

######Level2->Level3:
```
Need to read a file with spaces in it’s name. Let’s include the file name in quotes.

bandit2@melinda:~$ ls
spaces in this filename
bandit2@melinda:~$ cat "spaces in this filename"
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```

######Level3->Level4:
```
File which is necessery is in a hidden file in the inhere directory.

bandit3@melinda:~$ ls
inhere
bandit3@melinda:~$ cd inhere
bandit3@melinda:~/inhere$ ls -la
total 12
drwxr-xr-x 2 root    root    4096 Nov 14  2014 .
drwxr-xr-x 3 root    root    4096 Nov 14  2014 ..
-rw-r----- 1 bandit4 bandit3   33 Nov 14  2014 .hidden
bandit3@melinda:~/inhere$ cat .hidden
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

######Level4->Level5:
```
Password is available in the inhere directory and in human readable file format in the directory. Checking for the available files.

bandit4@melinda:~$ ls
inhere
bandit4@melinda:~$ cd inhere
bandit4@melinda:~/inhere$ ls -la
total 48
-rw-r----- 1 bandit5 bandit4   33 Nov 14  2014 -file00
-rw-r----- 1 bandit5 bandit4   33 Nov 14  2014 -file01
-rw-r----- 1 bandit5 bandit4   33 Nov 14  2014 -file02
-rw-r----- 1 bandit5 bandit4   33 Nov 14  2014 -file03
-rw-r----- 1 bandit5 bandit4   33 Nov 14  2014 -file04
-rw-r----- 1 bandit5 bandit4   33 Nov 14  2014 -file05
-rw-r----- 1 bandit5 bandit4   33 Nov 14  2014 -file06
-rw-r----- 1 bandit5 bandit4   33 Nov 14  2014 -file07
-rw-r----- 1 bandit5 bandit4   33 Nov 14  2014 -file08
-rw-r----- 1 bandit5 bandit4   33 Nov 14  2014 -file09
drwxr-xr-x 2 root    root    4096 Nov 14  2014 .
drwxr-xr-x 3 root    root    4096 Nov 14  2014 ..
bandit4@melinda:~/inhere$ file ./-*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@melinda:~/inhere$ cat ./-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```

######Level5->Level6:
```
Similar as the previous, with more files and new attributes of files to look through.

bandit5@melinda:~$ ls 
inhere
bandit5@melinda:~$ cd inhere
bandit5@melinda:~/inhere$ ls -la
total 88
drwxr-x--- 22 root bandit5 4096 Nov 14  2014 .
drwxr-xr-x  3 root root    4096 Nov 14  2014 ..
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere00
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere01
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere02
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere03
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere04
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere05
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere06
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere07
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere08
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere09
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere10
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere11
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere12
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere13
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere14
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere15
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere16
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere17
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere18
drwxr-x---  2 root bandit5 4096 Nov 14  2014 maybehere19
bandit5@melinda:~/inhere$ find ./ -size 1033c
./maybehere07/.file2
bandit5@melinda:~/inhere$ cat ./maybehere07/.file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```

######Level6->Level7:
```
The file can be anywhere on the server, but we are given it’s attributes. This is a job for find. The command attached to the end gets rid of garbage returns and allows viewing of our password file amongst several others with the same attributes.

bandit6@melinda:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password
bandit6@melinda:~$ cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```

######Level7->Level8:
```
Password needed for the next level is stored in the file data.txt next to the word millionth. Pipe grep is used to grep this.

bandit7@melinda:~$ ls
data.txt
bandit7@melinda:~$ cat data.txt | grep millionth
millionth	cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

######Level8->Level9:
```
Need to find a unique line among many available. Few commands should be piped together to do this. Note the commands do need to be in this order.

bandit8@melinda:~$ ls
data.txt
bandit8@melinda:~$ cat data.txt | sort | uniq -u
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```

######Level9->Level10:
```
Password for the next level is stored in the file data.txt among of few lines of human-readable strings starting with ‘=’ characters.

bandit9@melinda:~$ ls
data.txt
bandit9@melinda:~$ strings data.txt | grep '='
epr~F=K
7?YD=
?M=HqAH
/(Ne=
C=_"
I========== the6
z5Y=
`h(8=`
n\H=;
========== password
========== ism
N$=&
l/a=L)
f=C(
========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
ie)=5e
```

######Level10->Level11:
```
Password for the next level is stored in the file data.txt and it contains base64 encoded data. File is decorded.

bandit10@melinda:~$ ls
data.txt
bandit10@melinda:~$ base64 -d data.txt
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```

######Level11->Level12:
```
Password is encoded using simple rot13 encryption. And here we decode the password.

bandit11@melinda:~$ ls
data.txt
bandit11@melinda:~$ cat data.txt | tr a-zA-Z n-za-mN-ZA-M
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```

######Level12->Level13:
```
Password for the next level is stored in the file data.txt, repeatedly compressed hexdump file is available. It is necessary to create a directory under /tmp using mkdir. File should be decompressed untill we achive the correct format.

bandit12@melinda:~$ ls
data.txt
bandit12@melinda:~$ file data.txt
data.txt: ASCII text
bandit12@melinda:~$ mkdir /tmp/im
bandit12@melinda:~$ cd /tmp/im
bandit12@melinda:/tmp/im$ xxd -r ~/data.txt > data.txt
bandit12@melinda:/tmp/im$ file data.txt
data.txt: gzip compressed data, was "data2.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
bandit12@melinda:/tmp/im$ zcat data.txt > dataNew
bandit12@melinda:/tmp/im$ ls
data.txt  dataNew
bandit12@melinda:/tmp/im$ file dataNew
dataNew: bzip2 compressed data, block size = 900k
bandit12@melinda:/tmp/im$ bzip2 -d dataNew
bzip2: Can't guess original name for dataNew -- using dataNew.out
bandit12@melinda:/tmp/im$ ls
data.txt  dataNew.out
bandit12@melinda:/tmp/im$ file dataNew.out
dataNew.out: gzip compressed data, was "data4.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
bandit12@melinda:/tmp/im$ zcat dataNew.out > evenNewer
bandit12@melinda:/tmp/im$ ls
data.txt  dataNew.out  evenNewer
bandit12@melinda:/tmp/im$ file evenNewer
evenNewer: POSIX tar archive (GNU)
bandit12@melinda:/tmp/im$ tar -xvf evenNewer
data5.bin
bandit12@melinda:/tmp/im$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@melinda:/tmp/im$ tar -xvf data5.bin
data6.bin
bandit12@melinda:/tmp/im$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@melinda:/tmp/im$ bzip2 -d data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out
bandit12@melinda:/tmp/im$ ls
data.txt  data5.bin  data6.bin.out  dataNew.out  evenNewer
bandit12@melinda:/tmp/im$ file data6.bin.out
data6.bin.out: POSIX tar archive (GNU)
bandit12@melinda:/tmp/im$ tar -xvf data6.bin.out
data8.bin
bandit12@melinda:/tmp/im$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", from Unix, last modified: Fri Nov 14 10:32:20 2014, max compression
bandit12@melinda:/tmp/im$ zcat data8.bin > lost
bandit12@melinda:/tmp/im$ ls
data.txt  data5.bin  data6.bin.out  data8.bin  dataNew.out  evenNewer  lost
bandit12@melinda:/tmp/im$ file lost
lost: ASCII text
bandit12@melinda:/tmp/im$ cat lost
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```

######Level13->Level14:
```
Password for the next level is stored in /etc/bandit_pass/bandit14 and only can be read by user bandit14. Password for the next level is not provided, but the private SSH key can be used to log into the next level. SSH Key is essential.

bandit13@melinda:~$ ls
sshkey.private
bandit13@melinda:~$ ssh -i sshkey.private bandit14@localhost
Could not create directory '/home/bandit13/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is 05:3a:1c:25:35:0a:ed:2f:cd:87:1c:f6:fe:69:e4:f6.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit13/.ssh/known_hosts).

bandit14@melinda:~$ cat /etc/bandit_pass/bandit14
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```

######Level14->Level15:
```
Password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost. Telnet is used to connect to localhost on port 30000 and enter the password.

bandit14@melinda:~$ telnet localhost 30000
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr

Connection closed by foreign host.
```

######Level15->Level16:
```
Password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption. SSL commands are used.

bandit15@melinda:~$ openssl s_client -connect localhost:30001 -quiet
depth=0 CN = li190-250.members.linode.com
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = li190-250.members.linode.com
verify return:1
BfMYroe26WYalil77FoDi9qh59eK5xNr
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

read:errno=0
```

######Level16->Level17:
```
The password for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Only 1 server provide the next level password, Other server will echo back what you send to it.

bandit16@melinda:~$ nmap -p 31000-32000 localhost -sV

Starting Nmap 6.40 ( http://nmap.org ) at 2015-08-19 10:38 UTC
Stats: 0:00:16 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 40.00% done; ETC: 10:38 (0:00:24 remaining)
Nmap scan report for localhost (127.0.0.1)
Host is up (0.0010s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE VERSION
31046/tcp open  echo
31518/tcp open  msdtc   Microsoft Distributed Transaction Coordinator (error)
31691/tcp open  echo
31790/tcp open  msdtc   Microsoft Distributed Transaction Coordinator (error)
31960/tcp open  echo
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 41.30 seconds
bandit16@melinda:~$ echo `cat /etc/bandit_pass/bandit16` | openssl s_client -connect localhost:31518 -quiet                         
depth=0 CN = li190-250.members.linode.com
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = li190-250.members.linode.com
verify return:1
cluFn7wTiGryunymYOu4RcffSxQluehd

bandit16@melinda:~$ echo `cat /etc/bandit_pass/bandit16` | openssl s_client -connect localhost:31790 -quiet
depth=0 CN = li190-250.members.linode.com
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = li190-250.members.linode.com
verify return:1
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

read:errno=0
bandit16@melinda:~$ mkdir /tmp/im
bandit16@melinda:~$ cd /tmp/im
bandit16@melinda:/tmp/im$ touch sshkey.private
bandit16@melinda:/tmp/im$ vi sshkey.private
bandit16@melinda:/tmp/im$ ls
sshkey.private
bandit16@melinda:/tmp/im$ chmod 600 sshkey.private

bandit16@melinda:/tmp/im$ ssh -i sshkey.private bandit17@localhost
Could not create directory '/home/bandit16/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is 05:3a:1c:25:35:0a:ed:2f:cd:87:1c:f6:fe:69:e4:f6.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/bandit16/.ssh/known_hosts).

bandit17@melinda:~$ 
```

######Level17->Level18:
```
2 files are available in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and only one line is different between both the files passwords.old and passwords.new. Then the line which is different between both are found.

bandit17@melinda:~$ ls
passwords.new  passwords.old
bandit17@melinda:~$ diff passwords.new passwords.old 
42c42
< kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
---
> BS8bqB1kqkinKJjuxL6k072Qq9NRwQpR
```

######Level18->Level19:
```
Password for the next level is stored in File readme in the home directory. Unfortunately, .bashrc is modified which will logout when you logged in to bandit18.

Byebye !
Connection to bandit.labs.overthewire.org closed.

[root@localhost Desktop]# ssh bandit18@bandit.labs.overthewire.org cat readme
bandit18@bandit.labs.overthewire.org's password: 
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```

######Level19->Level20:
```
setuid binary in the home directory is used to get the access to the next level. Password for this level can be found in the usual place (/etc/bandit_pass).

bandit19@melinda:~$ ls
bandit20-do
bandit19@melinda:~$ ./bandit20-do
Run a command as another user.
  Example: ./bandit20-do id
bandit19@melinda:~$ ./bandit20-do id
uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11020(bandit20),11019(bandit19)
bandit19@melinda:~$ ./bandit20-do whoami
bandit20
bandit19@melinda:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```

######Level20->Level21:
```
setuid binary file is availble in home directory that does the following: Connection to localhost is established on the port you specify as a command line argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

bandit20@melissa:~$ ls
suconnect
bandit20@melissa:~$ ./suconnect
Usage: ./suconnect <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the
correct password from the other side, the next password is transmitted back.
 
#In 1st terminal do:
bandit20@melissa:~$ nc -l 3222
 
#In 2nd terminal do:
bandit20@melissa:~$ ls
suconnect
bandit20@melissa:~$ ./suconnect 3222
 
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
 
Read: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
Password matches, sending next password
```




