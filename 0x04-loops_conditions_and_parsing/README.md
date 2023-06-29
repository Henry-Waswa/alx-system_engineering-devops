# 0x04. Loops, conditions and parsing

## Resources:books:
Read or watch:
* [Loops sample](https://intranet.hbtn.io/rltoken/fRCmr2B_Ne-rQdFZdfUDcA)
* [Variable assignment and arithmetic](https://intranet.hbtn.io/rltoken/o8mucWW2XddN4MHiHSArkA)
* [Comparison operators](https://intranet.hbtn.io/rltoken/jN0bfG-Qpkg3aYJM-n3LHw)
* [File test operators](https://intranet.hbtn.io/rltoken/mYWUvI1VFqR_KWNWZngq7Q)
* [Make your scripts portable](https://intranet.hbtn.io/rltoken/Dyrnap2UC-LrzrmCOJRx8A)

---
## Learning Objectives:bulb:
What you should learn from this project:

* How to create SSH keys
* What is the advantage of using  #!/usr/bin/env bash over #!/bin/bash
* How to use while, until and for loops
* How to use if, else, elif and case condition statements
* How to use the cut command
* What are files and other comparison operators, and how to use them

man or help:

*    env
*    cut
*    for
*    while
*    until
*    if
---
## Learning Objectives

At the end of this project, you are expected to be able to explain to anyone, without the help of Google:
General

*    How to create SSH keys
*    What is the advantage of using #!/usr/bin/env bash over #!/bin/bash
*    How to use while, until and for loops
*    How to use if, else, elif and case condition statements
*    How to use the cut command
*    What are files and other comparison operators, and how to use them

## General Requirements

*    Allowed editors: vi, vim, emacs
*    All your files will be interpreted on Ubuntu 14.04 LTS
*    All your files should end with a new line
*    A README.md file, at the root of the folder of the project, is mandatory
*    All your Bash script files must be executable
*    You are not allowed to use awk
*    Your Bash script must pass Shellcheck (version 0.3.3-1~ubuntu14.04.1 via apt-get) without any error
*    The first line of all your Bash scripts should be exactly #!/usr/bin/env bash
*    The second line of all your Bash scripts should be a comment explaining what is the script doing

---
## Watch this:

* [What is a server?](https://www.youtube.com/watch?v=B1ANfsDyjeA)
* [What is data center?](https://www.youtube.com/watch?v=iuqXFC_qIvA&feature=youtu.be&t=33)

## Read this:

* [Server](https://en.wikipedia.org/wiki/Server_(computing)#Hardware_requirement)
* [What is Virtual MAchine (VM)](https://en.wikipedia.org/wiki/Virtual_machine)
* [What are Containers and why do you nedd them?](https://www.cio.com/article/2924995/what-are-containers-and-why-do-you-need-them.html)

---
## Shellcheck

[Shellcheck](https://github.com/koalaman/shellcheck) is a tool that will help you write proper Bash scripts. It will make recommendations on your syntax and semantics and provide advice on edge cases that you might not have thought about. Shellcheck is your friend! All your Bash scripts must pass Shellcheck without any error or you will not get any points on the task.

To install Shellcheck type:
```
sudo apt-get install shellcheck
```

For every feedback, Shellcheck will provide a code that you can use to get more information about the issue, for example for code SC2034, you can browse [SC2034](https://github.com/koalaman/shellcheck/wiki/SC2034).

---
## Shell

System engineering & DevOps

### Manpage

Most of Unix systems are managed by using Shell. Just as you need to know a minimum number of words to have a discussion in a language, you need to know a minimum number of commands to be able to easily interact with a system. Unix systems all have, sometimes with slight differences, the same set of commands. While it is not too hard to remember commands, it might be hard to remember all of their options and how exactly to use them. The solution to this is the man command. Let’s go through a part of the ssh one, as there are few elements to know to be able to read a man page:

```
NAME
ssh — OpenSSH SSH client (remote login program)

SYNOPSIS
ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec] [-D [bind_address:]port] [-E log_file] [-e escape_char] [-F configfile] [-I pkcs11] [-i identity_file] [-L [bind_address:]port:host:hostport] [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
[-Q cipher | cipher-auth | mac | kex | key] [-R [bind_address:]port:host:hostport] [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]] [user@]hostname [command]

DESCRIPTION
ssh (SSH client) is a program for logging into a remote machine and for executing commands on a remote machine. It is intended to replace rlogin and rsh, and provide secure encrypted communications between two untrusted hosts over an insecure network. X11 connections and arbitrary TCP ports can also be forwarded over the secure channel.
```

### Some tips:

*    The NAME will summarize what the command is doing. As it is usually super short, you might want to look at DESCRIPTION (bellow) if ever it does not gives clear enough information
*    The SYNOPSIS will help you to understand the structure of the command:
*        A shell command usually have this format: command options parameters
*        Options inside [] are optional
*        The string without [] are mandatory
*    ssh [-1246AaCfgKkMNnqsTtVvXxYy] [-D [bind_address:]port]
*        ssh is mandatory
*            -1246AaCfgKkMNnqsTtVvXxYy is optional
*            -D [bind_address:]port is optional (with bind_address: being itself optional within -D [bind_address:]port

### Commands

Here is the (non-exhaustive) list of commands & concepts you should master to be verbose with Unix systems:
```
awk # pattern scanning and processing language
basename # strip directory and suffix from filenames
bg # resumes suspended jobs without bringing them to the foreground
cat # print files
cd # change the shell working directory.
chmod # change file mode
chown # change file owner and group
crontab # maintain crontab files
curl # transfer a URL
cut # remove sections from each line of files
date # display or set date and time
dig # DNS lookup utility
df # report file system disk space usage
diff # compare files line by line
du # estimate file space usage
echo # display a line of text
find # search for files in a directory hierarchy
fg # resumes suspended jobs and bring them to the foreground
grep # print lines matching a pattern
kill # send a signal to a process
less # read file with pagination
ln # create links
ls # list directory contents
lsb_release # print distribution-specific information
lsof # list open files
mkdir # create
mv # move files
nc # arbitrary TCP and UDP connections and listens
netstat # print network connections, routing tables, interface statistics...
nice # execute a utility with an altered scheduling priority
nproc # print the number of processing units available
passwd # change user password
pgrep # look up processes based on name and other attributes
pkill # send signal to processes based on name and other attributes
printenv # print all or part of environment
pwd # print name of current/working directory
top # display Linux processes
tr # translate or delete characters
ps # report a snapshot of the current processes
rm # remove files or directories
rmdir # remove directories
rsync # remote file copy
scp # secure copy (remote file copy program)
sed # stream editor for filtering and transforming text
sleep # suspend execution for an interval of time
sort # sort lines of text file
ssh # OpenSSH SSH client (remote login program)
ssh-keygen # SSH key generation, management and conversion
su # substitute user identity
sudo # execute a command as another user
tail # output the last part of files
tar # manipulate archives files
tr # translate or delete characters
uname # Print operating system name
uniq # report or omit repeated lines
uptime # show how long system has been running
w # Show who is logged on and what they are doing
whereis # locate the binary, source, and manual page files for a command
which # locate a command
wc # print newline, word, and byte counts for each file
xargs # build and execute command lines from standard input
| # redirect standard output to another command
> # redirect standard output
< # redirect standard input
& # send process to background
```

### Shortcuts

Some handy shortcuts:
```
CTRL+A # go to beginning of line
CTRL+B # moves backward one character
CTRL+C # stops the current command
CTRL+D # deletes one character backward or logs out of current session
CTRL+E # go to end of line
CTRL+F # moves forward one character
CTRL+G # aborts the current editing command and ring the terminal bell
CTRL+K # deletes (kill) forward to end of line
CTRL+L # clears screen and redisplay the line
CTRL+N # next line in command history
CTRL+R # searches in your command history
CTRL+T # transposes two characters
CTRL+U # kills backward to the beginning of line
CTRL+W # kills the word behind the cursor
CTRL+Y # retrieves last deleted string
CTRL+Z # stops the current command, resume with fg in the foreground or bg in the background
```
---

### [0. Create a SSH RSA key pair](./0-RSA_public_key.pub)
Read for this task:

* [How do I set up SSH authentication keys in Linux or Mac?](https://askubuntu.com/questions/61557/how-do-i-set-up-ssh-authentication-keys)
* [How do I set up SSH authentication keys in Windows?](https://support.rackspace.com/how-to/generating-rsa-keys-with-ssh-puttygen/)

man: **ssh-keygen**

You will soon have to manage your own servers hosted on remote data centers. We need to set them up with your RSA public key so that you can access them via SSH.

Create a RSA key pair.

*Requirements:*

*    Keep the private key to yourself in a secure location, you will use it later to connect to your servers using SSH. Some storing ideas are Dropbox, Google Drive, password manager, USB key. Failing to do so will prevent you to access your servers, which will prevent you from doing your projects.
*    If you decide to add a passphrase to your key, make sure to save this passphrase in a secure location, you will not be able to use your keys without the passphrase

SSH and RSA keys will be covered in depth in a later project.

when you generate an rsa key two files are generated: "id_rsa",  "id_rsa.pub":

*    "id_rsa.pub" is the public key, It is the one that we are going to use at point 0 of the project, we must change its name.
*    "id_rsa": It is the private key and it is the one that must be kept in a confident place

### [1. For Holberton School loop](./1-for_holberton_school)
* Write a Bash script that displays Holberton School 10 times.

*    You must use the for loop (while and until are forbidden)

Note that:

*    The first line of my Bash script starts with #!/usr/bin/env bash (To be portable).
*    The second line of my Bash scripts is a comment explaining what it is doing.

### [2. While Holberton School loop](./2-while_holberton_school)
* Write a Bash script that displays Holberton School 10 times.

* You must use the while loop (for and until are forbidden)

### [3. Until Holberton School loop](./3-until_holberton_school)
* Write a Bash script that displays Holberton School 10 times.

* You must use the until loop (for and while are forbidden)

### [4. If 9, say Hi!](./4-if_9_say_hi)
* Write a Bash script that displays Holberton School 10 times, but for the 9th iteration, displays Holberton School and then Hi on a new line.

*    You must use the while loop (for and until are forbidden)
*    You must use the if statement

### [5. 4 bad luck, 8 is your chance](./5-4_bad_luck_8_is_your_chance)
* Write a Bash script that loops from 1 to 10 and:


*    displays bad luck for the 4th loop iteration
*    displays good luck for the 8th loop iteration
*    displays Holberton School for the other iterations

Requirements:

*    You must use the while loop (for and until are forbidden)
*    You must use the if, elif and else statements
*    
For the most curious:

*    [8 in the Chinese culture](https://freakonomics.com/2006/07/05/lucky-8s-in-china/)
*    [4 in the Chinese culture](https://freakonomics.com/2006/07/05/lucky-8s-in-china/)

### [6. Superstitious numbers](./6-superstitious_numbers)
* Write a Bash script that displays numbers from 1 to 20 and:


*    displays 4 and then bad luck from China for the 4th loop iteration
*    displays 9 and then bad luck from Japan for the 9th loop iteration
*    displays 17 and then bad luck from Italy for the 17th loop iteration

Requirements:

*    You must use the while loop (for and until are forbidden)
*    You must use the case statement

### [7. Clock](./7-clock)
* Write a Bash script that displays the time for 12 hours and 59 minutes:


*    display hours from 0 to 12
*    display minutes from 1 to 59

**Requirements:**

*    You must use the while loop (for and until are forbidden)

Note that in this example, we only display the first 70 lines using the head command.

### [8. For ls](./8-for_ls)
* Write a Bash script that displays:


*    The content of the current directory
*    In a list format
*    Where only the part of the name after the first dash is displayed (refer to the example)

**Requirements:**

*    You must use the for loop (while and until are forbidden)
*    Do not display hidden files

### [9. To file, or not to file](./9-to_file_or_not_to_file)
* Write a Bash script that gives you information about the holbertonschool file.

**Requirements:**

*    You must use if and, else (case is forbidden)
*    Your Bash script should check if the file exists and print:
*        if the file exists: holbertonschool file exists
*        if the file does not exist: holbertonschool file does not exist
*    If the file exists, print:
*        if the file is empty: holbertonschool file is empty
*        if the file is not empty: holbertonschool file is not empty
*        if the file is a regular file: holbertonschool is a regular file
*        if the file is not a regular file: (nothing)

### [10. FizzBuzz](./10-fizzbuzz)
* Write a Bash script that displays numbers from 1 to 100.

**Requirements:**

*    Displays FizzBuzz when the number is a multiple of 3 and 5
*    Displays Fizz when the number is multiple of 3
*    Displays Buzz when the number is a multiple of 5
*    Otherwise, displays the number
*    In a list format

### [11. Read and cut](./100-read_and_cut)
* help: read

Write a Bash script that displays the content of the file /etc/passwd.

Your script should only display:

*    username
*    user id
*    Home directory path for the user

**Requirements:**

*    You must use the while loop (for and until are forbidden)

### [12. Tell the story of passwd](./101-tell_the_story_of_passwd)
* Read:

*    [IFS (internal field separator)](http://www.tldp.org/LDP/abs/html/internalvariables.html)
*    [Understanding /etc/passwd](https://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)

The file **/etc/passwd** has already been covered in a [previous project](https://intranet.hbtn.io/projects/208) and you should be familiar with it. Today we will make up a story based on it.

Write a Bash script that displays the content of the file /etc/passwd, using the while loop + IFS.

Format: **The user USERNAME is part of the GROUP_ID gang, lives in HOME_DIRECTORY and rides COMMAND/SHELL. USER ID's place is protected by the passcode PASSWORD, more info about the user here: USER ID INFO**

**Requirements:**

*    You must use the while loop (for and until are forbidden)

### [13. Let's parse Apache logs](./102-lets_parse_apache_logs)
[Apache](https://en.wikipedia.org/wiki/Apache_HTTP_Server) is among the most popular web servers in the world, serving 50% of all active websites, no doubt that you will have to interact with it within your career.

As a Full-Stack Software Engineer, you have to master the art of parsing log files. Today we will do a simple parsing of [Apache log access files](./apache-access.log).

Today the Customer Support department reported that a user reported that the site is being “buggy”. Not being a detailed description, you want to have a look at the Apache logs and gather data about the traffic.

Write a Bash script that displays the visitor IP along with the [HTTP status code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) from the Apache log file.

Requirement:

*    Format: IP HTTP_CODE
*        in a list format
*        See example
*    You must use awk
*    You are not allowed to use while, for, until and cut
*    Download and commit the apache-access.log file along with your answers files

### [14. Dig the data](./103-dig_the-data)
* Now that you’ve parsed the Apache log file, let’s sort the data so you can get a better idea of what is going on.

* Using what you did in the previous exercise, write a Bash script that groups visitors by IP and HTTP status code, and displays this data.

**Requirements:**

*    The exact format must be:
*        OCCURENCE_NUMBER IP HTTP_CODE
*        In list format
*    Ordered from the greatest to the lowest number of occurrences
*        See example
*    You must use awk
*    You are not allowed to use while, for, until and cut
