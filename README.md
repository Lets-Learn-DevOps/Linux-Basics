# Linux-Basics

# Linux-HandNotes

### Linux Commands and Options 

There are 300+ flavors of Linux :
```
Kali Linux :  Majority ethical hacking ppl will use this Flavor
Corporate : RedHat , CentOS ,  Ubuntu , Fedora , IBM AIX , HP_Unix , Cisco Unix ,OEL.
```

What do we use in lab is CentOS 7 

## Linux Command Standard Syntax:

Command-name {options} {inputs} 
```
Options:
    - <Single-Character>
    -- <Single-Word>

Standard Option to all the commands is --help
    Ex: uname --help 
```


```Command line Syntaxes.```

```
$ command -options  
```

## Commands

In terminal, the first argument we give to execute is a command.

For example:

``` 
uname 
```
uname is a command and that is the first word of a command line syntax.


## Options

Certain commands are going to have options, Options in Linux Command line will be a second argument over the command line, Usually those options will be seen in three formats..
```
    <command>    -<single character> (Ex: -h , -v )
    <command>    --<single word> (Ex: --help , --version)
    <command>    -<single word> (Ex: -version, -help) 

 ```

For Ex :
``` 
uname -a   
uname --all 
```

# Inputs

Certain commands require inputs, Inputs are given with options in some commands and without options for some commands.

For Example:
 ``` 
ls stands for list
    $ ls /boot
    $ ls -d /boot
```

In above example, ls is a command -d is an option and /boot is an input. 
Given the command with and without option changes the behavior of the command execution.


### Hardware and Operating system Information

In general, when we purchase a new hardware like Laptops or Desktops we generally look into the configuration of the machine. So let us try to do the same for the server as well and this is minimum knowledge required while you are working on any machine either that is Desktop or Server.

So we need to login to the server to run the following commands to see the system details.
In Linux, everything is a file. So, it's all about reading respective files to know the properties


### To check the vendor of the operating system.

```
$ cat /etc/*release
```

### To check the CPU information

```
$ cat /proc/cpuinfo
```

### To check the memory information 
```
$ cat /proc/meminfo
```

###  To check the disk information
```
$ fdisk -l   or    lsblk
``` 

### To check the architecture whether it is 32bit or 64bit

```
$ uname -i

32 bit ->  i386/i586/i686 
64 bit ->  x86_64

PS Note: Starting CentOS 7, We don't have operating systems coming in 32 bit any more. Hence, we always see 64 bit.
With this information in hand you will have an idea of what you are dealing with and the specifications of that Linux machine. 

```



## Listing Files and Directories

# List Files

In windows OS, you generally see the list of files when you open a particular folder, But Linux is mostly command line and hence you may not see the files by default. Hence, you need to execute a command to check the list of files.

ls is a Linux shell command that lists directory contents of files and directories. Some practical examples of ls command are shown below.

```
Syntax: ls <Options> <Path>
```

Note that ls command works without an input i.e both the options and path are optional. It works with or without them.
```
$ ls -ld /opt
```

Get list of files and directories but it may not show hidden files.
```
$ ls
```

Get list of hidden files and directories.
```
$ ls -A
```

Get list of files with long format, usually shows properties of a file
```
$ ls -l
```

We can combine multiple options as well.
```
$ ls -Al
```
## NOTE: 
Giving multiple options depends on the command. ls accepts multiple options but it isn't applicable for all.


### Creating files

We can create files in multiple ways/commands in Linux. We will use `touch` command to create the file.
```
Syntax: $ touch <filename>
```
touch command by default creates an empty file.

```
$ touch file.txt
```

To check the file created.
```
$ ls -l
```
In the above ls command output you can see the file is an empty size file by referring the fifth colum.

touch command can create multiple files at a single go as shown.

touch sample notes.txt lambda.py

To check the file created.
```
$ ls -l
```
### Important Takeaways:

In Linux OS, there is no file-extensions. Extensions are given only for user understanding.
Also, linux commands and files are case sensitive.

```
training.txt and Training.txt are 2 different files as per the linux ( as it's case sensitive )
```


### Removing Files


In Linux to remove files we have `rm` command, We can also use unlink command which does the same thing yet rm is widely preferred and used command.

        Syntax: rm <filename>
```
$ rm fileName.txt
```

Now again when you list the files using ls command the sample file should be gone as you have removed it.
```
$ ls
$ rm -i fileName.txt
```

It may ask you for a prompt (yes/no) [Not all the times] to remove the files. You can suppress the prompt by adding -f option in the command.
```
$ rm -f fileName.txt
$ ls
```

Note: Be careful while removing a file as it deletes all the contents of the file and retrieving the lost data is not possible in most of the cases.
Thing you can explore.

How to remove multiple files ?
```
$ rm file1 file2
```

###  Copying Files

In Linux to copy a file we have cp command. Alternatively we have rsync but mostly we prefer to use cp command in general.
```

    Syntax: cp <source-file> <destination-file>

            $ cp notes.txt pages.txt
```

You can check whether the file has been copied or not by referring ls command output.

            $ `ls`

NOTE: If destination exists it will overwrite the file and in some cases it will ask you for a prompt (yes/no) to overwrite the file or not.


## Rename Files

### Renaming/Moving a File

In Linux, in order to change the name of a file we use mv command.

        Syntax: mv <source-file> <destination-file>

                $ mv notes.txt note.txt

You can check whether the file has been renamed or not by referring ls command output.

                $ ls

NOTE: Unlike Windows, Linux filesystem are Case-Sensitive ones, Meaning the file note.txt & NOTE.txt can be referred as two different files. But windows FAT & NTFS filesystem are Case-Insensitive, Meaning the file note.txt & NOTE.txt are same files and you cannot create multiple files with same name.

                $ mv note.txt NOTE.txt

You can check whether the file has been renamed or not by referring ls command output.

                $ ls

## NOTE: 
    If destination exists then it will overwrite the file and in some cases it will ask you for a prompt (yes/no) to overwrite the file or not.
    mv command intention is to move the file from one location to another yet we use mainly to rename the files as well.
