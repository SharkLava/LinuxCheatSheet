# Linux Cheat Sheet for Beginners
![wallpaperflare com_wallpaper(1)](https://user-images.githubusercontent.com/96528048/204434186-3f7bae4c-b0dd-46fc-8fa9-5283a148a530.jpg)

## Most Essential Commands
### `man`
- The `man` Command returns the Documentation of the Requested Command.
- `man <command_name>`
- Example: `man ls`
- Returns the Documentation of the `ls` Command.

### `--help` or `-h` flag
- A Flag is used in Conjunction with a Command  `gcc --help` or `gcc -h`
- Using this flag returns a Help Page which contains Functions relating to the Command
- Example: `gcc --help`
- Returns the Useful Functions of `gcc`
 
### `sudo` and `su` 
- `sudo` is a Package in GNU/Linux used for Creating Normal Users in Linux. Similar to users in Windows. 
- There are two types of Users in GNU/Linux `Standard User` and `Admin | Root`
- While installing or executing some Commands You'll need `Admin | Root Access` executing the Command with `sudo` provides you temporary `Admin | Root` access.
- `su` is the command which allows you to be root. If you have lots of things to do as `Root | Admin` and you are too lazy to type `sudo` every time, you can use `su` to gain root access for a longer time (Until you close the Terminal Windows in which you used the `su` command)

## The Essentials
### `cd`
- `cd` is used to traverse the filesystem from the terminal
- `cd <path>` will move the terminal to the defined path
- `cd ..` will move the terminal to the parent directory if it exists
- `cd /` will move the terminal to the root directory
- `cd ~` or just `cd` will move the terminal to the home directory 

### `ls`
- `ls` shows all the visible files and folders in directory. 
- `ls -a` shows all the hidden and visible files and folders in the directory.
- `ls -A` shows **almost** all the hidden and visible files and folders in the directory(It excludes the `.` which loops back to the current directory and the `..` which points to the parent directory)
- `ls -l` displays all the visible files and folders and lists them in tabular form with some extra information(like size, author, date modified, etc)

### `touch`
- `touch <filename>` creates an empty folder with the name specified

### `mkdir`
- `mkdir <foldername>` creates a folder with the specified name in the current location of the terminal.
- `mkdir -p <path_to_folder>` creates the folder in the path specified as well as all the missing folders in the path to the folder.

### `mv`
- `mv <source_path> <destination_path>` moves a file from the source_path to the destination_path
- `mv <path>/old_name <path>/new_name` will rename a file named `old_name` in the location `<path>` to `new_name`
    
### `cp` 
- `cp <source_path> <destination_path>` copies a file from the source_path to the destination_path
- `cp -r` is used to copy folders by recursively copying their contents
    
### `rm` 
- `rm <file1> <file2> <file3>` deletes the files mentioned
- **The Recycle Bin or Trash does not exist when it comes to deleting things from the terminal** so be careful with this command.
- `rm -f <file>` force deletes the file and overrides any warnings.
- `rm -r <folder>` recursively deletes the contents of a folder and finally deletes the folder too.
- **UNDER NO CIRCUMSTANCE SHOULD YOU RUN ANY OF THE FOLLOWING UNLESS YOU ARE ABSOLUTELY SURE ABOUT WHAT YOU ARE DOING**
    - `sudo rm -rf /` this will delete everything in your root directory
    - `rm -rf ~` this will delete everything in your home directory
- Running `rm -rf` with elevated priviliges in a dangerous location will most probably break your OS.
- Exercise caution.
   
### `grep`
- `grep` is used to search the content of a specified file or durectory for a given string or a regex
- `grep '<search_term>' <file>` searches for the `search_term` in the `<file>`
- `grep -i '<search_term>' <file>` will search for the `search_term` in a case insensitive way.
- `grep -r '<search_term>' <folder_path>` will search for the `search_term` recursively within the specified directory.
    
### `cat`
- `cat` allows the user to execute basic text modification from the terminal
- It is not a full blown editor like Vim or Emacs but it can read and append to files
- `cat <file>` will display the contents of the file 
- `cat >> <file>` will allow you to enter some text into the terminal. The entered text is then appeneded to the end of the file.


## The Extras
### `pwd`
- `pwd` returns the path to the active directory

### `top`
- `top` displays the processes running in real time. It also displays resource utilization and other information regarding the process.

### `pkill`
- `pkill <pattern>` kills the first processes with the string `<pattern>` in their name

### `pgrep`
- `pgrep <pattern>` returns the PID of all processes with the string `<pattern>` in their name

### `kill`
- `kill <PID>` terminates the process with the PID specified

## Useful for Bash Scripting

### `echo`
- `echo "Hello, World!"` will print Hello, World! on the terminal.

### `wc`
- `wc <file>` will print the number of words in a file
- `wc -l <file>` will print the number of lines in a file

### Piping data
- We can pass the output of one command to the input of another by using the `|` operator.
- `grep -r '<search_term>' <folder_name> | wc -l` will return the number of entries that match the search

## SSH
### `ssh`
- `ssh` is program used to log into and access a machine. It was designed as a more secure replacement to `telnet`.
- The commands that you type into your `ssh` shell terminal are excecuted on the host instead of the login shell
- `ssh user_name@host(IP/Domain_name)` will ssh into the specified host in the user `user_name`

### `scp`
- `scp` is Secure Copy, it is mostly used to copy files over ssh. 
- Its usage is very similar to `cp`, one key difference is that we need to mention the user and the hostname of the devices in the address.
- `scp -r us<er1@host1:home/Documents/ user2@host2:home/target_path` will copy the contents of the `Documents` folder in `user1`'s home directory in `host1` to the home directory of `user2` in `host2host`. 

## System Calls
### `fgets`
- `fgets()` is a system call in the `stdio.h` package.
- `fgets()` reads in at most one less than size characters from stream and stores them into the buffer pointed to by `s`. Reading stops after an EOF or a newline. If a newline is read, it is stored into the buffer. A terminating null byte (aq\0aq) is stored after the last character in the buffer.  
#### Example: 

``` c
#include <stdio.h>
int main() //Program that uses fget() to accept a string from the user and print it
{
    char buf[10];
    fgets(buf, 10, stdin);
    printf("%s\n", buf);
    return 0;
}
```
