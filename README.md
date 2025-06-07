# Linux-module

Overthewire bandit 

# bandit level 0 
solution 
 ssh bandit0@bandit.labs.overthewire.org -p 2220
passward :bandit0 

# bandit level 0 --> bandit level 1 
 Level Goal
The password for the next level is stored in a file called - located in the home directory
# solution 
once access to bandit0@bandit 
list file using LS 
use the cat comand - cat"readme" to read file 
 passward :  ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

#  bandit level 1 --> bandit level 2 
 Level Goal
The password for the next level is stored in a file called - located in the home directory
# soltuion 
connect to server using bandit1@bandit.labs.overthewire.org -p 2220    
passward : ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
once connected to server 
ls to list directory 
file name is - 
use cat ./- to read file , dont use cat "-"  as this mean read from standard input so cat doesnt interpret - as a file 
passward : 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

#  bandit level 2 --> bandit level 3
Level Goal
The password for the next level is stored in a file called spaces in this filename located in the home directory 
# solution 
ls 
then 
 cat "spaces in this filename"
passward : MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

# Bandit Level 3 → Level 4
Level Goal
The password for the next level is stored in a hidden file in the inhere directory.
# solution 
ls should show driectory inhere 
cd "inhere" to go into inhere directory 
ls -a to show all files including hidden 
cat "...Hiding-From-You" to list acount of that file , which should give you the passward 
 passward : 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

# Bandit Level 4 → Level 5
Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
# solution 
ls 
cd inhere 
strings ./*  as This command extracts human-readable ASCII and ./* this looks of all files in current directectory 
# solution 2 
file ./* - should show file07 as ascii text 
cat./-file07 = to show content of file 7 

passward :4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

# Bandit Level 5 → Level 6
Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable

# solution 
find . ! -executable -size 1033c = finds files that are not exexcutable and has size of 1033 
 cat ./inhere/maybehere07/.file2 - to read file 

passward: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

# Bandit Level 6 → Level 7
Level Goal
The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size

# solution 
find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null 
then cat /var/lib/dpkg/info/bandit7.password 
or 
 find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null -exec cat {} \;

find /= start from search from root 
type f = regular files 
size 33c = size of file 33 bytes 
- user bandit 7 and - group bandit6 = owned by user bandit7 and belong to group bandit 6 
2>/dev/null = redirect error messages to /dev/null since i cant access every folder 
exec cat {} \;= for each file found from resilt run cat command 

passward : morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

# Bandit Level 7 → Level 8
Level Goal
The password for the next level is stored in the file data.txt next to the word millionth

# solutuion 
find / -type f -name "data.txt" 2>/dev/null -exec grep "millionth" {} \;
find the file data .txt similar to previous level 
then use grep command to print out the line that contains millionth 
passward : dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

# Bandit Level 8 → Level 9
Level Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
# solution 
sort data.txt| uniq -u
passward :4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

# Bandit Level 9 → Level 10
Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
# solution 
strings data.txt|grep "="
strings data.txt = extract all human readable text 
grep "=" filter by lines that contain = 
passward : FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

# Bandit Level 10 → Level 11
Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data

# solution 
 cat data.txt | base64 -d
cat to concatenate abd base64 -d to decode file 
passward : dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

 # Bandit Level 11 → Level 12
Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

# solution 
 cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
read file using cat and decode using rot 13 

passward :  7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4 

# Bandit Level 12 → Level 13
Level Goal
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!

# solution 
mktemp -d 
cp ~/data.txt /tmp/tmp.dgxpX3z8du
then 
 mv data.txt file1
then dont if file is gzip, bzip2 or POSIX tar so we will start with gzip decompress 
 mv file1.txt file1.gz
gunzip file1.gz
still showing as ascii text looks like file is hexadump so i will convert back to binary 
xxd -r file1.gz>file2 

file file2 = shows its gzip 
mv file2 file2.gz 
gunzip file2.gz 
file 2 is now bzip 
so 
mv  mv file2 file2.bz
 bunzip2 file2.bz

now file is gzip rename and decompress again 
once done file show be posix tar -  mv file2 file2.tar
tar -xf file2.tar
file is posic tar but name as data5.bin  , so change name by - mv data5.bin data5.tar then tar -xf data5.tar
new file data6.bin which is bzip change name then bunzip 
its now posix tar so do the same thing again change name and decompress 
then its gzip called data8.bin show change name and decompress should give data8 file which contains the passward 
passward : FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn 

# Bandit Level 13 → Level 14
Level Goal
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on
# solution 
 ls 
 sshkey.private 
ssh -i sshkey.private bandit14@localhost -p 2220
# Bandit Level 14 → Level 15
Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.**#
# solution 
cat /etc/bandit_pass/bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS 
 cat /etc/bandit_pass/bandit14 | nc localhost 30000 to send passward to port 30000
passward : 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

# bandit Level 15 → Level 16
Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.

# solution 
originally tried this echo " 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo" | openssl s_client -connect localhost:30001
however this gave to much output so had to add -quite 
 echo "8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo" | openssl s_client -quiet -connect localhost:30001
passward: kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx 
# Bandit Level 16 → Level 17
Level Goal
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

# solution
nmap localhost -p 31000-32000 to find out which ports are opened 
 nmap localhost -p 31046,31518,31691,31790,31960 -sV -T4
this tells nmap to scan these ports and know service version on each port and time is go to be 4
dint use t5 as its to agressive and might miss data 
ports which are open and speak ssl = 31790 and 31518 
cat /etc/bandit_pass/bandit16
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
openssl s_client -connect localhost:31518 this is not correct one as it sends back whatever you send 
openssl s_client -connect localhost:31790 
 echo  "kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx" |  openssl s_client -connect localhost:31790 -quiet


