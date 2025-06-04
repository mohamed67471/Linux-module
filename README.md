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
mkdir temp 
cp ~/data.txt /tmp/tmp.NzsUCW4HjW$
then 
 mv data.txt file1
 




