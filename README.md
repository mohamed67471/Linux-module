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



