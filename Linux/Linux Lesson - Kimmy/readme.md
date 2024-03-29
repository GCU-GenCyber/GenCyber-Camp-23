# Beginners: Lesson 1 - Linux 101
## Root and File System

Log into Kali:
```
User: toor
Pass: root
```

It is important to know that in Linux **root** is similar to the Windows' **Administrator**. Those privileges are not given to every user, and we will go over privileges and permissions later. 

Right now, we are just going to learn how to look at Linux's file system. Find Kali’s version of File Explorer and explore the files. Don’t open anything, just look at file names and see how far back you can get into the files. Windows starts at the C drive, but where does Linux start?

Find the Root directory. What is in the root directory? 
(A directory is a folder that contains files)

As stated before, root is a user, like an admin. It’s the user with the most privileges. Just like in Windows, all of the files belonging to the user (Desktop, Documents, etc.) are under that user’s name. Take a minute to explore the file system and see if you can find any differences or similarities between Linux and Windows. 


## Settings

Find the Following Settings and Applications:

Desktop Background
- Change it to one of the pre-installed ones
Mousepad (Application)
- Open
- Write hello world!
- Name it hello and Save it to your Documents folder
- Exit 

## Terminal Usage vs. GUI

Continue to Explore Kali
What happens when you click on the tools? Well, most of them pull up what is called a terminal. Kali is mostly used via a terminal. Windows uses more GUI than Linux. What’s a GUI?
- Graphical User Interface
- all the nice windows that pop up when you click on an application

For example, when you click on the file system application, that’s a GUI. You have visuals to see what you’re doingSince Linux is mostly used via a terminal, how do we go through the file system without a GUI?
- Open up the terminal application on your machines.
- It is important to note, terminals don’t work like google. They are extremely case and spelling sensitive. 
- You need to know commands to be able to use the terminal.

## Commands for File Navigation

- pwd: tells you where you are
	- Remember how the user’s files are under the users name? We can still find those files and see them in the terminal

- ls : to see the files and folders that are in your current location (or file path)
	- All of the things in blue are directories
	- Those are the other folders that we can move to
 
__Remember the mousepad file you made earlier? What folder is the hello in? How do we get there to read it?__
- cd: change directory
	- cd Documents
	- ***LINUX IS CASE SENSITIVE!!*** 
	- Assume everything is lowercase unless you see otherwise, like a file or directory name

Use ls to list the files in your current directory, which should be documents. You should see the hello file you created. But, how do we read what it says?
- cat: will read the file
	- Do "cat hello" in the terminal

Now you know how to navigate through a file system. Here are some more examples of basic linux commands that are extremely helpful. 


mkdir : makes a directory
```
mkdir Files
```
<sub>This command will make a directory named Files in Your Current Location</sub>


rm : removes the file named after the command
```
rm hello 
```
<sub>This command deletes the file we created named hello (if you're in its current location)</sub>


touch : creates a file
```
touch hello 
```
<sub>This command creates a file in your current directory named hello</sub>


--help or -h : pulls up a help page for whatever application you ask
``` 
hydra --help 
```
<sub>This command will pull up a help page for a password bruteforcer called Hydra</sub>


man : pulls up manual/manpages for a tool
```
man hydra
```
<sub>This command will show a manual for a password bruteforcer called Hydra</sub>


cp : copies a file to a different file path
```
cp hello /root/Documents 
```
<sub>This command will move the file named hello to the specified path. The syntax is as follows "cp [FILENAME] [FILEPATH]"</sub>


mv : to move a file
```
mv hello /root/Documents
```
<sub>This command will move the file hello into the specified path. It is similar to cutting and pasting. The syntax is as follows "mv [FILENAME] [FILEPATH]"</sub>


mv: to rename a file
```
mv hello hello1 
```
<sub>This command renames a file. The syntax is as follows "mv [CURRENTFILENAME] [NEWFILENAME]"</sub>


find : to find a file in your computer
```
find / -name hello.txt 
```
<sub>This command will locate a file for you. The syntax is as follows "find [where to start searching from] [options] [what to find]"</sub>


### Extra Linux Rules
- Case Sensitive
 - You have to specify the path of where you want to go like /root/Documents or go into the documents folder to see anything in there
 - If you accidentally run something you aren't supposed to or want to stop, use __Ctrl+C__ end it

# Beginners: Lesson 2 - How to View Permissions
- File Permissions 
	- You can only access a File if you have permission to see it
	- As root, you can see or change anything you want
	- Not that you should, but you have the ability to
	- So how do you see file permissions

Find the hello.txt you created with Mousepad 
- Right click on it
- Click properties
- Click Permissions
You can see the owner, the owner’s group, and others who can see the file. It also specifies the access they have to that file (Read, Read & Write, etc.)

Now check for file permissions in a Terminal
- Open a terminal
- Enter 
```
ls --help
```
The - is a switch (or an option) that gives the command more specifics. There are two options that will help in this case. 
- a : shows all files, even hidden ones (Yes there are hidden folders, Windows has those too.)
- l : long listing format meaning more information
You can combine them both together so instead of using ls -l -a it’s ls -la

This gives you the 
- file permissions
- the owner (creator) of the file
- the group to which that owner belongs to
- the date of creation
				
# Beginners: Lesson 3 - How to View and Change Permissions
![alt text](https://github.com/GCU-GenCyber/GenCyber-Camp-23/blob/main/Linux/Linux%20Lesson%20-%20Kimmy/img/BasicPermissions.png)

The file type will appear as a **-** , **d**, or **i** : file, directory, or link

As seen in the picture, R W X means read, write, and execute.Those are the 3 permissions on Linux. Now, take a look at the hello file that we created. What does it say for the permissions?
- rw-r--r--
- **-** means it is a file
	
The first rw- means the user can read and write or modify it, no execute
- r-- means the group can only read it
- r-- means others can only read it
- The next two words are the others and group
			

To changing file permissions, the command for that is: chmod. 
```
chmod +x hello
```
<sub>The syntax is as follows: chmod [permission] [file_name]</sub>

There are three different parts to changing permissions. You must know the who, what, and which values can be used. For example, the who's are: 
- u: User, meaning the owner of the file.
- g: Group, meaning members of the group the file belongs to.
- o: Others, meaning people not governed by the u and g permissions.
- a: All, meaning all of the above.
Note: If the who is not specified, the change will be made to all users, groups, and others. 

The what values are as follows: 
- –: Minus sign. Removes the permission.
- +: Plus sign. Grants the permission. The permission is added to the existing permissions. If you want to have this permission and only this permission set, use the = option, described below.
- =: Equals sign. Set a permission and remove others.

The which values are as follows: 
- r:  The read permission.
- w: The write permission.
- x: The execute permission.
Note: A combination of all three of these will be used in the single [permissions] section. 

You can only chnage permissions if you have the permission to do so. root is always allowed. You also have to specify the permissions for each section. For example:
- chmod u=rwx,og=rwx hello (if you’re in Documents)
- No spaces, no capitals

You just changed file permissions to read, write and execute for the user, group, and others of hello. Note: if you named the hello file hello.txt, use that instead of just hello. Go ahead and ls -la again. What are the new permissions for the hello file?
- It should say -rwxrwxrwx

Try and use the chmod commands to set the permissions back to normal
- Make the user allowed to read and write 
- Make the members allowed to read
- Makes others allowed to read

### 5 Minutes Later...
- The permissions command should be 
``` 
chmod u=rw,g=r,o=r hello
```
<sub>It could also be chmod u=rw,og=r hello</sub>

Instead of using letters, there is also the octal format which represents privileges with numbers:
- r(ead) has the value of 4
- w(rite) has the value of 2
- (e)x(ecute) has the value of 1
- no permission has the value of 0

The privileges are summed up and depicted by one number. Therefore, the possibilities are:
- 7 – for read, write, and execute permission
- 6 – for read and write privileges
- 5 – for read and execute privileges
- 4 – for read privileges

As you have to define permission for each category (user, group, owner), the command will include three (3) numbers (each representing the summation of privileges).
- chmod u=rw,g=r,o=r hello command.
- chmod 644 hello
	- 6 would be read and write for users
	- 4 would be read for group
	- 4 would be read for others
	
Here is a table that shows how the numbers work to give permissions. 

![alt text](https://github.com/GCU-GenCyber/GenCyber-Camp-23/blob/main/Linux/Linux%20Lesson%20-%20Kimmy/img/chmod.png)

# Intermediate: Lesson 1 - More Commands!
Remember the command cd? What does it do? Well what if you want to change into a directory that isn't in your current directory. But, it is in your path. For example, let's say you're in /home/toor1/Documents. There is a command you can use to go back into toor1, also known as the parent directory because it is the one immeadiately above your current directory. To go back one directory. The command is as follows: 
```
cd ..
```
If you want to go to the very start of the computer, which is known as the root directory, the command is as follows: 
```
cd /
```
Now, what if you get lost and you just want to get back to your home directory where your Downloads, Desktops, Documents, etc. are? There is a command for that too. Wherever you are in the terminal, if you type the following command, it will take you back home. 
```
cd ~
```
### Here are some more helpful commands in Linux. 

Echo used to display lines of text or strings. It is mostly used in shell scripts so that when the script is ran, it repeats what is entered. To print text or a string on the terminal, use the syntax: echo [string] like so. 
```
echo "hello world!"
```
<sub> This will repeat the line you just entered. The example above did not use an option, but the normal syntax is as follows: echo [option] [string] </sub>

You can also write echo commands into files like so. 

![alt text](https://github.com/GCU-GenCyber/GenCyber-Camp-23/blob/main/Linux/Linux%20Lesson%20-%20Kimmy/img/IntermeadiateLesson1.png)

Nano is a text editor. You can use it to create a text file or to edit one. If you enter a file name that does not currently exist in that directory, it will create that file for you. Navigate to the hello file and enter the following. 
```
nano hello
```
You should always make sure your machines are up to date. To do this, you must have sudo privileges. If you do, enter this command to update your system. 
```
sudo apt update
```
As said before, sudo means super user do. It runs the command with super user privileges. This would work without sudo if you were logged in as root as well. This will only work if that user trying to use sudo has been given sudo privileges. 

You can use a command to show how much disk space you have available. 
```
df 
```
<sub> This shows available disk space in kilobytes, but you can use -m as a n option to show df in megabytes </sub>

On Windows, you can zip and upzip files by right clicking and choosing to compress or extract. On Linux, you can do that in a terminal. You can enter: 
```
zip hello
```
and then to unzip:
```
unzip hello
```
To view the current hostname that you are logged in as, you can enter the following: 
```
hostname
```
<sub> This will print the host name, which is the name of the computer. You could also do "hostname -i" which gives you your ip address</sub>

Another way to view your IP address is by entering:
```
ifconfig
```
<sub> This is similar to ipconfig in cmd for Windows. </sub>

The command to ping a website is the same as Windows. 
```
ping google.com
```
or you can use: 
```
ping 8.8.8.8
```
To view the current user that you are logged in as, you can use the following command. 
```
whoami
```
<sub> This will print the name of the current logged in user. </sub>

# Intermeadiate: Lesson 2
- What does rm -rf / do?
	- Removes with all directories and their contents with force
	- DONT DO IT
- But what is /?
	- / means the root directory
	- Which is everything, it holds all the files and directories

 ![alt text](https://github.com/GCU-GenCyber/GenCyber-Camp-23/blob/main/Linux/Linux%20Lesson%20-%20Kimmy/img/IntermeadiateLesson2.png)
 
Go back to the Documents folder
- Pwd and tell me where you are
- /root/Downloads : / means look at the very tippy top of the directory and follow the path from there
- Don’t get root directory confused with the root user, those are two different things. 

Navigate to /bin (Binaries). Do you see anything familiar?
- It holds the executables of a lot of commands
- It has ls, chmod, and more
- This means that commands are just executables that we are calling to 
- Linux Directory Structure Explained for Beginners (linuxhandbook.com)

![alt text](https://github.com/GCU-GenCyber/GenCyber-Camp-23/blob/main/Linux/Linux%20Lesson%20-%20Kimmy/img/IntermeadiateLesson3.png)
 
# Advanced: Tools
### Networking: 
- Ifconfig
- netdiscover
- Nmap
- Wireshark
### OSINT:
- Recon-ng
- Google Dorking
### Cryptography/Hashing:
- CyberChef
- Learn how to hash
- Then hash cat or jtr
### Digital Forensics:
- Autopsy
- FTK Imager
- CSI Linux
- Volatility
