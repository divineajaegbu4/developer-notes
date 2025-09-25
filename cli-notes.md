# Command Line Essentials for Beginners

- `pwd` : Print Working Directory
- `cd /`: Root directory or file system(absolute path)
- `cd`: Home directory
- `whoami`: Remind me of my username
- `~`: Home directory
- `NB`: Instead of writing `cd /home/username/Documents`, it’s better and cleaner to `cd ~/Documents`
- Absolute path: Starts from `/` (root)
- Relative path: Starts from where you're now
- Home directory: Your personal folder(`~`), which is part of the `absolute path: /home/username`

## Creating Folders and Files

- `mkdir -p /temp/tutorial or temp/tutorial`: Creates temp if it doesn't exit, then creates tutorial inside it (no error if they already exist)
- `NB`: The meaning of -p is "Create parent directories as needed". It is called an "option or a switch or flag".
- `mkdir /temp/tutorial or temp/tutorial`: Fails if temp doesn't already exist, because -p option was not used

## Sub-folders

- `mkdir -p temp/root temp/eyes temp/mouth`: root, eyes, and mouth are under `temp` folder
  
## Files

- `touch file` : Create empty file
- `echo "text" > file` : Create/overwrite file
- `echo "text" >> file`: Append to file
- `cat file`: Display file content; can merge files
- `Example: cat file > or >> file`: Merge files
- `less file`: Scrollable file viewer

## Wildcards

- `*`: Zero or more characters
- `?`: Exactly one character
  
## Redirection

- `>`: Overwrite file
- `>>`: Append to file

## Case Sensitivity

Linux treats uppercase and lowercase differently
`a.txt != A.TXT != A.txt`
`NB`: Best practice: Lowercase for normal files, uppercase for special files

## Viewing and Checking

- `ls`: list files/folders
- `ls -R`: Shows all sub-folders recursively
- `ls -a`: Hidden files
- `cat`: Quick content view
- `less`: Scrollable view, allows searching
- `ls -l`: show full details of the directory or files both the permission OR it is used for checking permission and ownership of a file or directory.

## Saving and Viewing Command Output

- `ls > output.txt`: Saves the list of files/folders in the current directory into output.txt(overwrites if its exist).
- `cat output.txt`: Displays this saved content on the terminal
`NB`: If you do `ls > output.txt` and then `cat output.txt`. What it will do is that, it will list all the folders/files with the output.txt in the current directory.

## Moving and Manipulating files

- ### Mv command (Move/Rename)
  
     > `mv file1 file2`
      >  - if `file2` doesn't exit: Renamefile1 to file2
      > - if `file2` exist: Overwrite file2 with file1
  
- ### Mv file directory

    `mv file1 dir2`: Move the file into the directory

- ### Mv directory directory
  
    >`mv dir1 dir2`
      > - if `dir2` doesen't exist: Rename dir1 to dir2
      >  - if `dir2` exist: Move dir1 inside dir2

## Copy Files

- `cp file1 file2`: Copy file1 into file2 (overwrites if exists)
- `cp file directory`: Copy the file into the directory
- `cp -r dir1 dir2`: Copy a whole directory and its contents
  
## Remove Files and directories

- `rm file`: Delete a file
- `rm -r directory`: Remove directory and its contents
- `rm -ri directory`: Interactive removal(asks before each delete)
- `rm -rf directory`: Force remove everything(no prompt)
- `trash-put file.txt`: Moves file.txt to your trash directory
- `trash-put directory`: Moves directory to your trash directory
- `trash-restore`: Restore your directory or file from trash
- `rm -r -i -I`: Ask once

## Wildcards and multiple files

- `mv dir1/* .`: Move everything from dir1 into current directory
- `mv file1 file2 file3 dir1`: Move multiple files into dir1
- `cp *.txt dir2`: Copy all `.txt` files into dir2
  
`NB`: rm -r -i -I

- `r`: Remove directories recursively(with all contents)
- `i`: Interactive mode - asks before moving to every file
- `I`: Less intrusive interactive - asks once if you're removing more than 3 files or recursively

## Backup Script

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

## Chmod (change mode)

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
