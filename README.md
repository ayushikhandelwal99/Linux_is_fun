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
