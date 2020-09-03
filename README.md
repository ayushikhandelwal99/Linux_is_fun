# Linux_is_fun
This repo is consists of notes and theory answers of many questions of sessions of my training 

### 001 
 ` This was an introductory session about how to set up fedora in your system ` 
  
### 002
```
. kernal
	driver management and loding is done by kernal
	it interects with the hardware
	it can limit the ressources
	core part of any os

. NT kernal
	used in all os by microsoft
	.exe format

. Darwin kernal
	used in all os by  apple
	.dmg format

. Linux
	.rpm (redhat package management) format (Rhel, oracle,Centos, Fedora, cloud linux, etc. more than 600)
	.deb format (Ubuntu, Debian, Mint, Kali/ Backtrack, etc. more than 600+)
	. installer name is anaconda

Q-->WHERE exactly linux is used?
 solution--> EX:- openwrt.org
```

### 003
```
There are 3 ways to access any os
 ->GUI, CLI, emergency based
 - GUI stands for graphical user interface
 - CLI stands for command line interface

any application can be accessed by click or typing
In all every application is controlled by either click or text
```

### 004
```
* windows  	|      linux    |      Mac
	  	|	     	|
   C folder   	|      /        |      /
   users	|      home     |     users
  system32 	|      bin       |     bin     	(internal command)

*to create a new user in fedora useradd or adduser both will work
```

### 005
```
*File creation --> using gedit or touch ,(vi , vim,nano,pico,emacs)text editors
*Remove Process (if you have a file it doesnt matter file is empty or not you can remove it but in case of directory if it is empty you can remove it but if it is not empty you cant remove it)
*rm if created for deliting files.
*rmdir deletes directory
*Vim is most powerful text editor
*tmp is shared by all users on a machine

*Shell (interpreter)
	bash (bourne again shell)
	sh
	tcsh
	csh
	ksh

fedora has default shell as bash , it also having supported shell
	-there is a file /etc/shells
PATH (capacity of path variable is equivalent to the os like C drive in windows and we can custamise its size)
	/usr/bin
	/usr/sbin
	/usr/local/bin
	/usr/local/sbin

type of command
	1. dependent on PATH variable--> external command
	2. not dependent on PATH variable --> internal command (cd,echo,exit,etc.)

Q -->pv command
solution--> pv allows a user to see the progress of data through a pipeline, by giving information such as time elapsed, percentage completed (with progress bar), current throughput rate, total data transferred, and ETA. To use it, insert it in a pipeline between two processes, with the appropriate options.
syntax:- pv [OPTION] [FILE]
```

### 006
```
*history 
!number --> runs the command on that number
!letter --> checks bottom to up and runs the first command it encounter with that letter
echo $HISTSIZE gives the size of history

*HIDDEN FILES in linux
.bash_history (to store all history data)
.bashrc
.bash_profile (both files to store variables permanantly)
 {a file starts with "." in linux is hidden} to check then we need to "ls -a" and graphically we have to Ctrl+H
 {after changing these hidden files we have to load it via source command "source location"}
 
Q --> What is the technical difference between .bashrc and .bash_profile
solution -->bash_profile is executed for login shells, while . bashrc is executed for interactive non-login shells. When you login (type username and password) via console, either sitting at the machine, or remotely via ssh: . bash_profile is executed to configure your shell before the initial command prompt.
	    Things that are specific to your login session should go inside .bash_profile. Things that is specific to bash shell itself should go to .bashrc.
	    {Let us consider an example. Imagine a situation where you want some event to happen when somebody logs in. May be send an API call/e-mail alert with user details and other system statistics as soon as the user logs in. 
If you add such logic inside .bashrc, it will unnecessarily trigger that event, even if the user launches a new terminal (which is not a login). So it is better to add such things inside .bash_profile rather than .bashrc.
}

*script command records the after commands untill you stop it using exit command (i.e. it stores both commands and outputs)

*by aliasing we can run a big command by just one word

Q --> how do i delete a perticular command from history such that it will not show even history -d number
(condition: you have to do it all in one terminal without closing it  though you can open another terminal)
solution -->history -d $((HISTCMD-1)) && history -d [line entry number]
	 Of course you could also use this command to run another command without it getting logged to the history file if you were so inclined;
	  # history -d $((HISTCMD-1)) && [type_your_command_here_and_execute]
	   Actually we are deleting the recent command just after execution by HISTCMD - 1

Q --> scriptreplay command
solution --> scriptreplay [-t] timingfile [typescript] [divisor]
	     Play back terminal typescripts, using timing information


*useradd -s /sbin/nologin(or we can use /bin/false) u2 {this will make user u2 but give it nologin shell so it can't be loggedin means it is not allowed to interect with shell} --> it means you are not giving login permision to anybody except u2.
*we can change this setting by assigning login shell usermod -s /bin/bash u2
```

### 007
```
*using env command we can see the environment variable
*username@hostname  PS1 variable me likha hota h
*PS1="DelVex: ---- >>" this way we changed the presentation of [\u@\h \w]\$ 
*stty can be used to change control signals {intr from cont + c to a or eof from exit to something else}{  stty --help}
* stty [signal] [newsignal]

Q--> why to start a file with shebang
solution--> it tells us how the code should be interpreted

*  ./ means pwd
* script can run using bash filename, after execution per ./filename or you can wright the entire path
SHELL SCRIPTING
-for print do echo
-for variable just write variable_name = value there is no data type
-for input from user read variable_name
-we also can use read -p "msg" variable_name
-for time delay between msgs use sleep seconds
```

### 008
```
* a command is a code or a script
* By Default, it runs the code as bash interpreter and if we want to run another code, we will need to define the environment type to be used e.g., /usr/bin/python "

Q--> who decides what are the uses of #,!,$ or <<
solution--> interpreter or compiler

Q--> how to make commands?
solution--> create a file < [code]
	    make it executable and put it inside path

* # only is comment
* #! it is shebang

Q--> When to use $ and `` (back quotes)
solution--> $ for variable and `  for command

Qjgd --> Try CTRL+ALT+F3 in fedora and login with that and print echo $0

NOTE: $ and ``    works with ''(double quote) but not '(single quote)

* compiler has three modes {ignorance, debug, execute}
  ignorance : module , comment
  execute: everything except ignorance and debug
(compiler reads everything)

* for multiline comment in bash we use <<marker   --data--    marker

* SHELL SCRIPTING
 - input comes in two types : 
 - inline input:
	echo $number   (the argument at that number after file name)
	echo $0 will give files path itself jisne ye code chlaya
	echo $@ means all arguments after file name
	echo $# means number of argument
	echo $* same as $@
 - for multiline inputs we can use ( Q -- khte kya h inhe --)
	read -d "deliminator" -p "msg" variable  {enter deliminator when done with the input}

 - if [  condition  ] then
	echo
   elif [  condition  ] then
	echo
   else
	echo
   fi
```

### 009
```
Q--> without any command file kaise bnaoge?
solution-->      >  or >>

* tr is used for translation(EX: cat | tr 'a-z' 'A-Z')

*Redirection of output
	- in a file  command > filename 
		{ > is overwritten if another output is redirected in same }{> ye file bnayega hi bnayega , bhot jiddi h delete krke bnayega agr exist kr rhi h to }
	  	{>>  is appended if another output is redirected in same}{already h to nhi bnegi ,nhi h to bn jayegi}
		{if the command not found then nothing is gonna redirect and file will remain same}
		{there are two pipes one for correct output(pipe number1) and one for error(pipe number 2)}{command >filename is same as command 1>filename, pipe number 1 is default when using > or >>}{& before > or >> redirects both}
		{/dev/null is blackhole of linux}
	
	- in another terminal (using tty command we can check terminal file location and then redirect it)
	- in a directory

	- in ram (using | pipe line)
		{ command   | command   jo left hand side se input le ske}

	- in a mail

* wc can be used to count words lines and characters using -w, -l , -c
```

### 010
```
- in another system(prerequisite IP/TCP/Port number)
	*setup the connectivity between two system using host only network or bridge network
 	 and check if the networks are on the same subnet must be able to ping the other system connected to the network. 
	*[ ifconfig / ip a s / ip addr show ] command can be used to check the IP address . 
	* If your IP ranges from 192.168 then you can use the command such as ip a s | grep 192.168* [ This command will also attach the ip you are looking for ]
	*ping IP of another machine when both are connected to same wifi / Hotspot
	*first to create a socket (IP:port)
	*receiver always starts the socket first
	*in linux NetCat utility can be used to create socket. 
	*command is nc -l 8888    (-l for listen) on receiver first. 
	*nc Ip_of_receiver 8888
	*if we want that sender can not interept server then we can use
	(nc -l 8888 -k) {this is for sending output to receiver}
	*for sending to receiver "command | nc IP 8888"
	*if we want to execute command from receiver side then {nc -l 8888 -k | /bin/bash -e} by this we can control the receiver system from sender.


Q--> nc and ncat:
solution-->nc : arbitrary TCP and UDP connections and listens	 
	 syntax : nc [-46DdhklnrStUuvzC] [-i interval] [-p source_port] [-s source_ip_address] [-T ToS] [-w timeout] [-X proxy_protocol] [ -x proxy_address[           :port]] [hostname] [port[s]]
	{Unlike telnet(1), nc scripts nicely, and separates error messages onto standard error instead of sending them to standard output, as telnet(1) does with some.}

Q--> grep
solution--> grep, egrep, fgrep - print lines matching a pattern
	    grep [options] Pattern [file..]
	    grep [options] [-e Pattren | -f File] [File..]

Q--> head and tail
solution-->head [option] [file] --> outputs first part of files
	   tail [option] [file] --> outputs last part of files

*grep (it's a language to filter the output){general regular expression pattern}
	grep -i -n word file location (-i for selecting both caps ans small and -n is for line number)
	^word for lines startingwith this word
	word$ for lines ending with this word
	-v gives lines where that word is not present
```

### 011
```
* cat : stdin lena and stdout dena
* for input the sign in < 
	- ` cat  /tmp/ok.txt`  here "<" is default

*festival command: Festival is a general purpose text-to-speech system. As well as simply rendering text as speech it can be used in an interactive command mode for testing and developing various aspects of speech synthesis technology. Festival has two major modes, command and tts (text-to-speech).{EX: cat /var/log/dmesg | festival --tts}

Q--> output of "echo $x + 1" where x=100
solution--> 100  + 1

*for mathematical expressions in shell scripting we can use
	-  y=$(($x+1)) 
	- expr $x + 1

*expr command: The expr command in Unix evaluates a given expression and displays its corresponding output.
	- for multiplication * must be escaped { $ expr 5 \* 3}
	
*factor command: The factor command in Linux is used to print the prime factors of the given numbers, either given from command line or read from standard input. The numbers given through standard input may be delimited by tabs, spaces or newlines.

Q-->Why when using for loop for useradd takes too much time but password change  do not?
solution-->

*seq command: seq command lets you print a sequence of numbers.
	- syntax {  seq [options] specification  }
* ` echo "password" | passwd user_name  --stdin`   asks for password only one time 
*ping -c 3 site : it will ping only 3 times
*firefox url & : this will open url in firefox

*LOOPS
     - for
     1  for((i=1;i<10;i++))
          do
	date
          done        
     2  for i in something
           do
	date
           done
	
     - while [ condition ]
        do
              date
        done
```

### 012
```
Data management in linux

*data management is a utility
*in /etc/passwd every row is delimeted by \n and every column is seperated by colon(:)

*awk --> Awk is a scripting language used for manipulating data and generating reports.The awk command programming language requires no compiling, and allows the user to use variables, numeric functions, string functions, and logical operators.
1. AWK Operations:
(a) Scans a file line by line
(b) Splits each input line into fields
(c) Compares input line/fields to pattern
(d) Performs action(s) on matched lines
syntax: awk options 'selection _criteria {action }' input-file > output-file

*gawk-->
*can be used to :
Scans a file line by line.
Splits each input line into fields.
Compares input line/fields to pattern.
Performs action(s) on matched lines.
Transform data files.
Produce formatted reports.
Format output lines.
Arithmetic and string operations.
Conditionals and loops.
syntax: gawk [POSIX / GNU style options] -f progfile [--] file ...
	gawk [POSIX / GNU style options] [--] 'program' file ...

*cut --> a command for cutting out the sections from each line of files and writing the result to standard output. It can be used to cut parts of a line by byte position, character and field.
syntax:    cut OPTION... [FILE]...
           cut -d "delimiter" -f (field number) file.txt

*grep-->The grep filter searches a file for a particular pattern of characters, and displays all lines that contain that pattern. The pattern that is searched in the file is referred to as the regular expression (grep stands for globally search for regular expression and print out).
syntax: grep [options] pattern [files]

*sed-->SED command in UNIX is stands for stream editor and it can perform lot’s of function on file like, searching, find and replace, insertion or deletion. Though most common use of SED command in UNIX is for substitution or for find and replace.
	- SED is a powerful text stream editor. Can do insertion, deletion, search and replace(substitution).
	- SED command in unix supports regular expression which allows it perform complex pattern matching.
syntax: sed OPTIONS... [SCRIPT] [INPUTFILE...]

*locate-->locate command in Linux is used to find the files by name. There is two most widely used file searching utilities accessible to users are called find and locate. The locate utility works better and faster than find command counterpart because instead of searching the file system when a file search is initiated, it would look through a database.
syntax: locate [OPTION]... PATTERN...

*find-->The find command in UNIX is a command line utility for walking a file hierarchy. It can be used to find files and directories and perform subsequent operations on them. It supports searching by file, folder, name, creation date, modification date, owner and permissions. By using the ‘-exec’ other UNIX commands can be executed on files or folders found.
syntax:  find [where to start searching from] [expression determines what to find] [-options] [what to find]

*less-->jitni bdi screen husme sbse phle data show kr dega. enter for line change and space for page change

*more-->jitni bdi screen husme sbse phle data show kr dega. enter for line change but here space will quit the file

*wildcard is kind of  some notation like $, *, ^
*regex {like a pattern matching algorithm} is having its pattern where it uses wildcards to do some automation

*NR: NR command keeps a current count of the number of input records. Remember that records are usually lines. Awk command performs the pattern/action statements once for each record in a file.
```

### 013
```
Compression
*it means data representation {data size to iska mtlb kbhi tha hi nhi}
*it can both increase the size and decrease the size
*compression capability se upr compress krne pr size increase ho jati h

*compression techniques
	- zip
	- bzip
	- gzip
*by gunzip we can unzip the file
*compressor vo hi accha hota h jo compression and decompression dono almost same rate se kre
*compression can be only judged by the type of data
```

### 014
```
Backup and Recovery
*to take backup in linux use ` TAR`  and in windows it is ` RAR` 
* RAR and TAR are methods used to archive not compress {like taking the data and putting it into one box}
*tar -cvf filename.tar files_locations --> to create tar file
*tar -tvf filename.tar  --> to view data inside tar with their permissions
*tar -xvf filename.tar --> if you deleted data from its location but want it back{extracting data}
*tar -xvf filename.tar  -C location  --> if you want to extract all data in some location
*tar -cvzf filename.tar.gz files_locations  --> if you want to compress the data too
*tar -xvzf filename.tar.gz --> will decompress and unarchive the data
*if you want to compress it by bz2 then use tar -cvjf filename.tar.bz2

Q--> why we need archive even when we can store all that data in a directory
solution--> 1. execute {as directory can have executable files and directories so any virus or program can run this even if the data is non active}
	2. network access {directory can be accessed from network}
	3. transfer {directory cannot be emailed you have to convert it in archive or by any other technology}
	
User Management
*categories of users
	- guest/ Nobody
	- System user
	- Non admin user/ non privileged user
		- normal user
	- root/ admin
		- user having all privileges

*for creating users in rpm format os we generally use useradd and in deb format os we generally use adduser

*if we don't assign password to the created user then it can't be accessed by either CLI or GUI

*user login methods
	- shell {su - username}{jisse hm doosre user ki home diretory me hi land kre agr - nhi use kiya to jis directory me current user ki h usi me land krenge and if vha vo dir nhi h doosre user ke andr to ommand to run ho jayegi vha but u can't create data there}
	- GUI

*useradd username creates 10 changes when run and if you create those 10 changes then you can create user without useradd command
	- /etc/passwd me user ki entry
	- /etc/shadow {jha sare users ke password hote h}
	- /etc/group {group name of user}
	- /etc/gshadow {password of groups}
	- /home/username {create a folder here}
	- secure home directory
	- /var/spool/mail/username {mail box is something jha sare email store honge}
	- /etc/skel me jo data h vo user me copy ho jata h
	- access of PATH variable
	- kernal interaction 
	
*yes command:The yes command outputs the same string, STRING, in a constant stream. If STRING is not specified, the word it repeats is "y". yes dates back to a time before Unix commands included the "force" (-f) option, which for many commands is the same as answering "yes" to all prompts.

*mailbox file:MBOX is a file extension for a text file used to organize and store e-mail messages. MBOX stands for MailBOX. The MBOX file is the most common format for storing email messages on a hard drive.
```

### 015
```
*diff -u shows the diferences between two files

*Virtual terminal: A Virtual Terminal is a full-screen terminal which doesn't run inside an X window (unlike the terminal window on your graphical desktop). Virtual terminals are found on all GNU/Linux systems, even on systems which don't have a desktop environment or graphical system installed.

*finger command: Finger command is used in Linux and Unix-like system to check the information of any currently logged in users from the terminal. It is a command-line utility that can provide users login time, tty (name), idle time, home directory, shell name, etc.

*Under /etc/passwd
1. username
2. linkto password i.e. /etc/shadow {here x is a notation by linux, its like a soft link or shortcut}
3. UID(userid): it is power of that user
	- it ranges between 0 - 65535
	- UID 0: root
	- UID 1000 - 60000: not root user
	- UID 1-999 & 60001- 65535: system user/dedicated user
4. GID(groupid)
5. comment field- kuch bhi likh do .. like info about user
6. users home directory : user ko kha bhejna h login pr
7. default shell


*Under /etc/shadow {only root can open it}
1. username
2. actual password {the format of the password is hash}
	- hash is a one directional approach
	- their are so many algos to do hashing
-- to identify which hash algo is used by your linux you can go to /etc/login.defs
--$1 -->MD5
--$5 -->SHA 256
--$6--> SHA 512

3. no. of days since last password change
	- days from 1 jan 1970
4. minimum no. of days to change password {itne din se phle password wapas change nhi kr skte}
	- 0 means their is no expire date : kbhi bhi change krlo

5. maximum no. of days to change password {forcefully ask for password change}
	- 99999 means kbhi nhi change krna	

*chage -l username : will give all details about user
```

### 016
```
6. no of warning days before your password expire

7. max number of days to change the password {mtlb itne din bad password expire ho jayega}{mtlb aapko 5th khtm hone ke bad itne din milenge password change krne ke liye and if change nhi kiya to password expire ho jayega} {root se change krwa skte h isme}

8. number of days for account expire

9. future reserve {agr kuch aaya future me to}

** shadow file /etc/login.defs file se default data uthata h


*under /etc/group
1. groupname
2. x 
	- link to /etc/gshadow file
3. group id
4. member list

*under /etc/gshadow
1. group name
2. password
3. reserve
4. member list

*busybox: Busybox allows you or programs to perform actions on your phone using Linux (copied from Unix) commands. ... The Android kernel is a modified version of the Linux kernel (that is why the Android kernel must always be open source). Busybox gives functionality to your phone that it does not have without it. Also known as swiss army knife of linux.

```

### 017
```
Linux file system permissions
1. general permission  (read , write, execute)
2. advanced permissions(sticky bit, sgid, suid, acl)

*accessing a file or directory means
- read(r=4)
- write(w=2)
- execute(x=1)

* every file and directory have their inode table which consists of their permissions
*their are 7 types of file in linux

*in inode table
1. type of file
2. permission for owner (next 3)
3. permission for group (next 3)
4. permission for others (next 3)
5.  .(dot) means general linux permission {their are other too}
6. number of links {soft link and hard link} 
7. owner name : represented by u
8. group: represented by g
9. size of file or folder
10. date and time of last access or modify
11. file or folder location


*owner can be more than one
*others are represented by o
* a stands for all {a-permission}
*we can set permissions by 'u+permission' for user and similar for others(o) and group(g) too
* or we can use numeric values like 755

##SECURITY TYPES
- DAC (discretionary access control)
	-general {r,w,x,advanced [owner,group,others]}
	-extended {}
- MAC
- PAM
 
```

### 018
```
##DAC

#general permissions
//r,w,x
*for changing owner and group respectively
*chown name_of_owner name_of_file
*chgrp name_of_group name_of_file
*chown  owner:group  file_name   //can change both owner and group

*primary and secondary group
	- user bnate time jo group bnta h vo primary grp hotah.
	- agr kisi or grp ka part bhi bnadete h us usr ko .. to vo nya grp secondary grp hota h

*lid command: The lid or libuser-lid command displays information about groups containing user name, or users contained in group name. This command requires sudo privileges. You should run the libuser-lid command instead of the lid command on newer systems.

*umask : whenever we create a file or folder in linux to usko default kya permission deni h ye umask decide krta h
*umask = max permission - permission given 
*umask ki value /etc/bashrc me define hoti h
*umask ka first bit special permissions ke liye h

//Advanced permissions
*sticky bit  +t  or it can be applied by (1) ==>1770 {770 are previous one's} {same directory me bhot sare user kaam kr rhe ho to vo khudke alawa kisi ka bhi kaam change na kr paye}

*sgid g+s  or it can be applied by(2) ==>2770  {set group id} {jitne bh users group me kaam kre un sare kaam ka group vo hi bne jisme vo file h mtlb vo hi group inherit ho jaye
}
[both sticky bit and sgid can be applied by 3770 i.e. (1+2)]
*group inheritence {sgid} for setting a common group to all the members of that group
```
