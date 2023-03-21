# Beginners: Lesson 1

Log into Kali using Root and toor

	Explain what root is: like admin

Find Kali’s version of File Explorer and explore the files

Don’t open anything just look at file names

See how far back you can get into the files

Find Root file

What is in the root file?

Root is a user, like an admin. It’s the user with the most privileges. Just like in Windows, all of the files (Desktop, Documents, etc.) are under that user’s name. 

Find the Following:

Settings
  	    Desktop Background
            Change it to one of the pre-installed ones
 	    Mousepad
	        Open
     	    Write hello world!
            Name it hello and Save it to your Documents folder
            Exit
    Explore Kali
        What happens when you click on the tools?
            Most of them pull up a terminal
	        Kali is mostly used via a terminal
	        Windows has more GUI than Linux
	            What’s a GUI?
       	        Graphical User Interface Examples (conceptdraw.com)
       	        All the nice windows that pop up when you click on an application
      	        When you click on the file system, that’s a gui
       	        You have visuals to see what you’re doing
       	        Since Linux is mostly Terminal, how do we go through the file system without a GUI?
	Teach how to navigate that same file system but in a terminal
        Terminals don’t work like google
        They use commands to work
        Commands to Tech for File Navigation: 
	        Pwd: tells you where you are
	            Remember how the user’s files are under the users name? We can still find those files and see them in the terminal
	        ls : to see the files of the path you are in
	            Go over file path if needed
	            All of the things in blue are directories
	            Those are the other folders that we can move to
	            What folder is the hello in? Documents
	            How do we get there?
	        Cd: change directory
	            cd Documents
	            LINUX IS CASE SENSITIVEAssume everything is lowercase unless you see otherwise, like a file or directory name
	            Ls again, list the files
	            You should see hello
    	        How do we read what it says?
	        Cat: will read the file
	            Do cat hello
	            Congrats you did it!
    Extra Linux Rules:
	    Case Sensitive
 	    You have to specify a path like /root/Documents or go into the documents folder to see anything in there
   	    If you accidentally run something you arent supposed to use Ctrl+C end it

Lesson 2
	File Permissions 
		You can only access a File if you have permission to see it
		As root, you can see or change anything you want
		Not that you should, but you have the ability to
		So how do you see file permissions
	Find the hello Mousepad again 
		Right click on it
		Click properties
		Click Permissions
		You can see the owner, the owner’s group, and others who can see the file
			It also specifies the access they have to that file (Read, Read & Write, etc.)
	Now check for file permissions in a Terminal
		Open a terminal
		Use ls --help
			The - is a switch that gives the command more specifics
			--help will pull up a menu that shows all of your options 
			There are two that will help in this case 
				-a : shows all files, even hidden ones
					Yes there are hidden folders, Windows has those too
				-l : long listing format meaning more information
				You can combine them both together so instead of using ls -l -a it’s ls -la
			This gives you the 
				file permissions
				the owner (creator) of the file
				the group to which that owner belongs to
				the date of creation
				Linux File Permissions Tutorial: How to View and Change Permission (phoenixnap.com)
					the image didnt come through
				The file type can be a -, d, or i: file, directory, or link
				Rwx means read, write, execute
				Those are the 3 permissions on Linux
		Look at hello
		What does it say for the permissions?
			-rw-r--r--
			- means it is a file
			The first rw- means the user can read and write or modify it, no execute
			R-- means the group can only read it
			R-- means others can only read it
			The next two words are the owner and group
			
Lesson 3
●	Changing file permissions
○	The command for that: chmod
○	You type chmod [permission] [file_name]
■	You can only do this if you have the permission to do so
■	Since you are root, it’s allowed
○	You have to specify the permissions for each section. For example:
■	chmod u=rwx,g=rwx o=rwx hello (if you’re in Documents)
●	No spaces, no capitals
■	You just changed file permissions to read write and execute for the user, group, and owner of hello
■	Go ahead and ls -la again
■	Now hello should say -rwxrwxrwx
■	Try and use the chmod commands to set the permissions back to normal
●	Make the user allowed to read and write 
●	Make the members allowed to read
●	Makes others allowed to read
■	5 Min Later
●	Should be chmod u=rw,g=r,o=r hello
●	Instead of letters, the octal format represents privileges with numbers:
○	r(ead) has the value of 4
○	w(rite) has the value of 2
○	(e)x(ecute) has the value of 1
○	no permission has the value of 0
●	The privileges are summed up and depicted by one number. Therefore, the possibilities are:
○	7 – for read, write, and execute permission
○	6 – for read and write privileges
○	5 – for read and execute privileges
○	4 – for read privileges
●	As you have to define permission for each category (user, group, owner), the command will include three (3) numbers (each representing the summation of privileges).
○	chmod u=rw,g=r,o=r hello command.
○	chmod 644 hello
●	At some point cd . and cd ..
○	Explain what . and .. is
●	More commands: mkdir, rm, touch, --help and man (manual), cp filename filepath, mv to rename or mv filename filepath, and locate 
Intermediate:
Lesson 1
●	echo and cat
○	 
●	nano hello.txt
●	sudo apt update
○	Sudo just runs the command with root privileges so this would work without sudo if you were logged in as root as well
●	df 
○	Shows available disk spaces
○	Can use -m to show in megabytes
●	zip and unzip
○	zip and unzip hello
●	chmod 
○	You can add individual permissions by using +r, +w, or +x to a file
●	hostname
○	Prints host name
○	hostname -i gives you your ip address
●	ping google.com or 8.8.8.8
Lesson 2
●	What does rm -rf / do?
○	Removes with all directories and their contents with force
○	DONT DO IT
○	But what is /?
■	/ means the root directory
■	Which is everything, it holds all the files and directories
 
●	Go back to the Documents folder
○	Pwd and tell me where you are
○	/root/Downloads : / means look at the very tippy top of the directory and follow the path from there
○	Don’t get root directory confused with the root user, those are two different things
●	Open /bin (Binaries)
○	See anything familiar?
○	It holds the executables of a lot of commands
○	It has ls, chmod, and more
○	This means that commands are just executables that we are calling to 
○	Linux Directory Structure Explained for Beginners (linuxhandbook.com)
 
Advanced:
●	Ifconfig
●	netdiscover
●	Nmap
●	Recon-ng
●	CyberChef
●	Learn how to hash
○	Then hash cat or jtr
●	Wireshark
●	Digital Forensics:
○	Autopsy
○	FTK Imager
○	CSI Linux
○	Volatility