 
bash_exercises
====

bash exercises in the book of 《Bash Guide For beginner》

-----


Chapter 1. Bash and Bash scripts
----
1 . Where is the bash program located on your system?

    $ which bash
    /bin/bash

2 .  Use the --version option to find out which version you are running.

    $ bash --version
    GNU bash, version 4.3.48(1)-release (x86_64-pc-linux-gnu)



3 .  Which shell configuration files are read when you login to your system using the graphical user interface and then opening a terminal window?

    ~/.bashrc

4 .Are the following shells interactive shells? Are they login shells?

+ A shell opened by clicking on the background of your graphical desktop, selecting “Terminal” or such from a menu.

+ A shell that you get after issuing the command ssh localhost.

+ A shell that you get when logging in to the console in text mode.

+ A shell obtained by the command xterm &.

+ A shell opened by the mysystem.sh script.

+ A shell that you get on a remote host, for which you didn't have to give the login and/or password because you use SSH and maybe SSH keys.


5 .Can you explain why bash does not exit when you type Ctrl+C on the command line?

6 . Display directory stack content.

    $ echo $DIRSTACK

7 . If it is not yet the case, set your prompt so that it displays your location in the file system hierarchy, for instance add this line to ~/.bashrc:

export PS1="\u@\h \w> "

8 . Display hashed commands for your current shell session.

    $ ls /bin

9 .How many processes are currently running on your system? Use ps and wc, the first line of output of ps is not a process

    $ echo $(( $(ps -aux |wc -l ) -1 ))


10 . How to display the system hostname? Only the name, nothing more!

    $ echo $HOSTNAME



-----
Chapter 2. Writing and debugging scripts
====
1 .Write a script using your favorite editor. The script should display the path to your homedirectory and the terminal type that you are using. Additionally it shows all the services started up in runlevel 3 on your system. (hint: use HOME, TERM and ls /etc/rc3.d/S*)

[1.solution]()

2 .Add comments in your script.

3 .Add information for the users of your script.

4 .Change permissions on your script so that you can run it.

5 .Run the script in normal mode and in debug mode. It should run without errors.

6 .Make errors in your script: see what happens if you misspell commands, if you leave out the first line or put something unintelligible there, or if you misspell shell variable names or write them in lower case characters after they have been declared in capitals. Check what the debug comments say about this.




