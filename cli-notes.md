# 🖥️ Command Line Essentials for Beginners

- `pwd` : Print Working Directory
- `cd /`: Root directory or file system(absolute path)
- `cd`: Home directory
- `cd -``: (previous directory):This will take you to the previous directory you were in.
- ``date``: Print date, time, months etc...
- ``ls -la or al``: Shows list and hidden files at the same time
- ``!!``: Run the last command you previouly executed.
- ``file filename``: Used to find out what type of file a file is
- `whoami`: Remind me of my username
- `~`: Home directory
- `NB`: Instead of writing `cd /home/username/Documents`, it’s better and cleaner to `cd ~/Documents`
- Absolute path: Starts from `/` (root)
- Relative path: Starts from where you're now
- Home directory: Your personal folder(`~`), which is part of the `absolute path: /home/username`


## ⌨️ CTRL Shortcuts
- ``CTRL + R``: Reverse search - It is used for searching through your command history
- ``CTRL + G``: Cancel search and return prompt


## 📂 Creating Folders and Files

- `mkdir -p /temp/tutorial or temp/tutorial`: Creates temp if it doesn't exit, then creates tutorial inside it (no error if they already exist)
- `NB`: The meaning of -p is "Create parent directories as needed". It is called an "option or a switch or flag".
- `mkdir /temp/tutorial or temp/tutorial`: Fails if temp doesn't already exist, because -p option was not used

## Sub-folders

- `mkdir -p temp/root temp/eyes temp/mouth`: root, eyes, and mouth are under `temp` folder
  
## 📄 Files

- `touch file` : Create empty file
- `echo "text" > file` : Create/overwrite file
- `echo "text" >> file`: Append to file
- `cat file`: Display file content; can merge files
- `Example: cat file > or >> file`: Merge files
- `less file`: Scrollable file viewer

## ✨ Wildcards

- `*`: Zero or more characters
- `?`: Exactly one character
  
## 🔁 Redirection

- `>`: Overwrite file
- `>>`: Append to file

## 🔍 Case Sensitivity

Linux treats uppercase and lowercase differently
`a.txt != A.TXT != A.txt`
`NB`: Best practice: Lowercase for normal files, uppercase for special files

## 💾 Viewing and Checking

- `ls`: list files/folders
- `ls -R`: Shows all sub-folders recursively
- `ls -a`: Hidden files
- `cat`: Quick content view
- `less`: Scrollable view, allows searching
- `ls -l`: show full details of the directory or files both the permission OR it is used for checking permission and ownership of a file or directory.

## ✅  Saving and Viewing Command Output

- `ls > output.txt`: Saves the list of files/folders in the current directory into output.txt(overwrites if its exist).
- `cat output.txt`: Displays this saved content on the terminal
`NB`: If you do `ls > output.txt` and then `cat output.txt`. What it will do is that, it will list all the folders/files with the output.txt in the current directory.

## 🔄 Moving and Manipulating files

- ### Mv command (Move/Rename)
  
     > `mv file1 file2`
      >  - if `file2` doesn't exit: Renamefile1 to file2
      > - if `file2` exist: Overwrite file2 with file1
  
- ### Mv file directory

    `mv file1 dir2`: Move the file into the directory

- ### Mv the directory and its contents

`mv -i dir1 dir2`: Move the whole directory and its contents into dir2 (asks before overwriting)

- ### Mv directory directory
  
    >`mv dir1 dir2`
      > - if `dir2` doesen't exist: Rename dir1 to dir2
      >  - if `dir2` exist: Move dir1 inside dir2

## 📑 Copy Files

- ``cp file1 file2``: Copy file1 into file2 (overwrites if exists)
- ``cp file directory``: Copy the file into the directory
- ``cp -r dir1 dir2``: Copy a whole directory and its contents
- ``cp -i``: The system will ask for comfirmation before overwriting an existing file
  
##  ❌ Remove Files and directories

- `rm file`: Delete a file
- `rm -r directory`: Remove directory and its contents
- `rm -ri directory`: Interactive removal(asks before each delete)
- `rm -rf directory`: Force remove everything(no prompt)
- `trash-put file.txt`: Moves file.txt to your trash directory
- `trash-put directory`: Moves directory to your trash directory
- `trash-restore`: Restore your directory or file from trash
- `rm -r -i -I`: Ask once

## 🔗 Wildcards and multiple files

- `mv dir1/* .`: Move everything from dir1 into current directory
- `mv file1 file2 file3 dir1`: Move multiple files into dir1
- `cp *.txt dir2`: Copy all `.txt` files into dir2
  
`NB`: rm -r -i -I

- `r`: Remove directories recursively(with all contents)
- `i`: Interactive mode - asks before moving to every file
- `I`: Less intrusive interactive - asks once if you're removing more than 3 files or recursively

## 💾 Backup Script

1. Create the script file
    `nano backup.sh`: This open a nano file named backup.sh file where to write our script

2. Inside nano, write this:
     `cp $1 $2.bak`
     - `cp`: copy
     - `$1`: The first argument you pass when running the script.
     - `NB`: If you run `./backup.sh important_data.txt`, you will see `important_data.txt.bak` because `$1.bak`. The script copies it to a new file with `.bak` added e.g important_data_txt.bak

## Save and Exit in nano

- `CTRL + O`: Enter(to save)
- `CTRL + X`: Exit

## Make it executable

- `chmod`: change mode
- `chmod 744 backup.sh`

## Run it

>`touch important_data.txt`
>`./backup.sh important_data.txt`
Now you will see:
`important_data.txt (the original)`
`important_data.txt.bak (backup copy)`

`NB`: Scripts are like rebots that do repeated jobs for you
`$(dollar sign)`: The only real sign used in shell to access variables/arguments. You can't replace it with another

## Clear Step

1. Create the script file
    `nano backup.sh`

2. Inside backup.sh, write
    `cp $1 $1.bak`

3. Make it executable
    `chmod 744 backup.sh`

4. Run it
    > `touch experiment.txt`
    `./backup.sh experiment.txt`

5. Result 🔥🔥
   

    > `experiment.txt(original)`
    `experiment.txt.bak(copy)`

## 🔐 Chmod (change mode)

It is used in linux to change file permission(read, write, and excute)

- `u`: user(owner)
- `g`: group
- `o`: others
- `a`: all

1. Symbols for Permissions

- `r`: read
- `w`: write
- `x`: execute

2. Add/Rename Permissions

- `chmod +x file`: Add execute permission
- `chmod +w file`: Add write permission
- `chmod u+x file`: Add execute owner only.
- `chmod g-r file`: Remove read from group

3. Set Exact Permission with `=`

>  `chmod u=wr, g=r, o=file`:wner = read/write, group = read, others = none

`=`: means set exactly these permission (remove any others not listed)

In short:

- Use `+` or `-` to add/remove permission
- Use `=` to set exact permission
- Use numbers for a shortcut

4. Permission are represented by numbers

>- `r(read): 4`
>- `w(write): 2`
>- `x(execute): 1`

e.g To get the owner for full access
4 + 2 + 1 = 7
`chmod 744 file`

## 🔎 Find Command

It searches for files and directories.

#### Basic Syntax
> ``find <path> [options]``
> ``e.g find Documents -name "*.txt" or find /home -type d -name myFolder``

 #### ⚙️ Common Options:

- `` -type f:`` Only regular files
- ``-type d:`` Only directories
- ``-iname "*.txt":`` Case-insensitive name match. Ignores uppercase or lowercase
- ``-name "*.txt" (pattern):`` Match file name
- ``-size +1k:`` Files bigger than IkB
- ``-user $user:`` Files owned by you
- ``-perm 644:`` Files with specific permission
- ``-mtime -2:`` Files modified in last two days
- ``-exec <command> {} \; : `` Run a command on each file found

###### -Size

- ``K:`` bytes
- ``K:`` kilobytes
- ``M:`` megabytes
- ``G:`` gigabytes

###### Prefix meaning

- ``+:`` Larger than the size
- ``-:`` Smaller than the size
- ``no prefix:`` Exactly equal to the size

##### Meaning of prefixes of -mtime

- ``+N:`` Modified more than N days ago
- ``-N:`` Modified less than N days ago
- ``N:`` Modified exactly N days ago

## 🧩 Grep Command

It searches content of the files

#### Basic Syntax

```bash
grep [options] "pattern" <file(s)>``
e.g grep "Divine" *.txt

### Notes

1.  Search inside all files that end with .txt in the current directory.

2. Look for the text “Divine” in those files.

3. It does not search directories, only the files that match *.txt.

```

#### ⚙️ Common Options

- ``-l:`` Show only filenames containing the pattern
- ``-L:`` Show filenames that do NOT contain the pattern
- ``-i:`` Ignore case(case-insensitive)
- ``-v:`` Show lines that do NOT match
- ``-n:`` Show line numbers with matches

##### Tip:

- ``-v:`` Works on lines
- ``-L:`` Works on files

#### Combine Find + Grep

```bash

find Documents -type f -name "*.txt" -user $USER -exec grep -l "backup" {} \;

### Notes

1. Finds .txt files in the Documents directory.

2. Only includes files owned by your user ($USER).

3. Searches for the text "backup" inside those files.

4. Prints the names of files that contain the text.

```

### Example: replace spaces with new lines in a file

``tr " " '\n' <  file.txt``

## A bit of Plumbing

### ``wc -``  Word count

It counts lines, words, characters, and longest line

``e.g wc -l file.txt``

##### Options

- ``-l:`` Count lines
- ``-w:`` Count words
- ``-c:`` Count bytes
- ``-m:`` Count characters
- ``-L:`` Length of the longest line

``NB: Pipelines(|)``

### ``Uniq -`` Uniq Lines

It removes consecutive duplicate lines
``e.g uniq -c file.txt``

##### Options

- ``-c:``  Show counts of duplicate
- ``-i:`` Ignore cases(case-insensitive)
- ``-u:`` Show only unique lines

### ``Sort -`` Sort Lines
It sorts lines alphabetically or numerically
``e.g sort -u file.txt``

##### Options
- ``-f:`` Ignore case (case-insensitive)
- ``-r:`` Reverse order
- ``-n:`` Numeric sort
- ``-u:`` Remove duplicate
- ``-t 'DELM':`` Set delamiter
- ``-c:`` Check if already sorted

``e.g cut -d ' ' -f2 file.txt``

``Key idea:`` These commands can be combined using pipes(|) to analyze text files, count words, find unique entries, sort, and search patterns efficiently.

``man - `` Stands for "manual"

``man <command> e.g man ls``

``NB:`` It shows the documents or help page for other commands in linux. It is a built-in instruction book for your computer.


## Command Line and Superuser

1. #### Command Line
    - Always to tell your computer what to do by typing commands
    - Sometimes faster or more powerful than clicking icons

2. #### 👑 Superuser(root)

- The superuser has all powers on the computer:
    - Can delete or change any file
    - Can shutdown or restart system
    - can change network and security settings
    - Danger: Mistakes can break the whole system


3. #### ⚠️ Why not login as root

- Always being root is risky - one wrong command can destroy everything
- Others can also misuse the system if you leave it open

4. #### 🔑 Su Command

- ``su -`` "Switch user"
    - Can switch to root or another user
    - Danger: After switching, all commands have super powers.

5. ####  🛡️ Sudo Commands
- ``Sudo -`` "Do this command as superpower"
    - Safer than root because it only gives superpowers for one command at a time.
    - Always ask yourself: "Do I understand this computer, before using ``sudo``"

``e.g sudo apt update``: Refresh the package list
``e.g sudo apt upgrade``: Install available updates

1. #### 🛠️ Installing Software Safely

- Use official repositories(like apt on Ubuntu) when possible.
- Be careful with commands from untrusted sources (curl, wget, pip, npm)

7. #### ⏱️ Rules
🛡️ Safely Rules:

- Don't login as root
- Avoid using ``su`` unless necessary
- Use ``sudo`` for single commands
- Only run commands you understand
- Installing from official sources is safest. 


## Session commands in linux

- Restart now - sudo reboot
- Shutdown now - sudo shutdown down
- Shedule shutdown - sudo shutdown +10
- Shedule restart - sudo shutdown -r +5
- Logout - logout
- Lock screen - gnome-screensaver-command -l
- Suspend/sleep - systemctl suspend
- cancel shutdown - sudo shutdown -c
- shutdown and restart later - sudo shutdown -r +5
- exist - to close the terminal


## ⏱️ Match any single character from inside the brackets

1. ### Range inside brackets

`` ls file[1-3].txt -`` Matches file1.txt, file2.txt, and file3.txt. Do not match file4.txt

2. ### Character Set

`` ls *[abc].txt - `` Matches any ``.txt`` file ending with a, b. or c

3. ### Navigation with ! and ^

`` ls file[!1].txt -`` 
- Matches file2.txt, file3.txt, etc
- Excludes file1.txt

## ❓Difference blw help and man command

- ``help <command>``: It is used for built-in commands in the shell. ``e.g cd, echo, pwed, history etc...``. It gives a short description of how command works.

###### WHILE


- ``man <command>``: It is used for all commands(both built-in and external programs like ``ls, cp,mv, git). It opens a detailed manual page with sections

``e.g``

``type<command> - `` Provides a brief description of command-line programs

## 🔗 Alias in linux

An alias is a shortcut for a longer command. ``e.g alias co = "command"``

##### Types
  
- `Temporary alias`: Only works in the current terminal session. When you reboot it will go.

- `Permanent alias`: Stays even after reboot. add it to ~/.bashrc or ~/.zshrc is using zsh shell.

## 🎯 Useful Commands

1. Show all aliases

`alias`

2.Remove an alias

unalias name

3. Reload aliases after editing ~/.bashrc

source ~/.bashrc

``e.g alias update = "sudo apt update && sudo apt upgrade"
