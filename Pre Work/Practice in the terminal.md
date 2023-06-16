# Outline

1. The Command Line
2. Basic Navigation
3. More About Files
4. Manual Pages
5. File Manipulation

## The command Line

A command line, or terminal, is a text based interface to the system. You are able to enter commands by typing them on the keyboard and feedback will be given to you similarly as text.

## Navigation

First command to not is **pwd** which prints current directory

There are 2 types of paths we can use, absolute and relative. Whenever we refer to a file or directory we are using one of these paths. Whenever we refer to a file or directory, we can, in fact, use either type of path (either way, the system will still be directed to the same location).

Absolute paths specify a location (file or directory) in relation to the root directory. You can identify them easily as they always begin with a forward slash ( / )

Relative paths specify a location (file or directory) in relation to where we currently are in the system. They will not begin with a slash.

some shortcuts worthy of mention:

- ~ (tilde) - This is a shortcut for your home directory. eg, if your home directory is /home/ryan then you could refer to the directory Documents with the path /home/ryan/Documents or ~/Documents
- . (dot) - This is a reference to your current directory. eg in the example above we referred to Documents on line 4 with a relative path. It could also be written as ./Documents (Normally this extra bit is not required but in later sections we will see where it comes in handy).
- .. (dotdot)- This is a reference to the parent directory. You can use this several times in a path to keep going up the hierarchy. eg if you were in the path /home/ryan you could run the command ls ../../ and this would do a listing of the root directory.

next command to take note of is **cd** which changes directory.

ps: when in doubt tap TAB to auto-fill your current line

## More about Files

Under the hood every thing is a file in linux, even your keyboard is a file that the system only reads from

linux doesnt rely on extensions in the file name to properly handle the file. A me.png can be changed to me.txt or just me and linux would still process that this is an image

linux is also case sensitive so be aware whenever you're trying to access a folder or file and remember if it was written with any upper cases. also keep note of this when writing commands

since linux treats spaces as breaking points between commands we must be aware of that and make sure to use '' to signal that this is one entity and not me trying to pass multiple arguments to a single command

to see hidden files in linux use the **-a** with the **ls** command to request for hidden files to show

## Manual Pages

**man <command>**

Look up the manual page for a particular command.

**man -k <search term>**

Do a keyword search for all manual pages containing the given search term.

**/<term>**

Within a manual page, perform a search for 'term'

**n**
After performing a search within a manual page, select the next found item.

## File Manipulation

we can use **mkkdir** to create a new directory(folder) in linux

options that can be used with **mkdir** are **-p** which lets **mkdir** know to make parent directiories as needed. and **-v** which simply put makes **mkdir** tell me the result of the command line execution

**rmdir** removes directories from linux. keep in mind a directory must be empty in order to be able to delete it

**rmdir** supports **-p** and **-v**

**touch** can be used to create an empty file

**cp** can be used to copy a file and takes two arguments. first the source then the destination

**-r** makes it so the copying is recursive meaning its copying directories altering the default behavior of **cp**

**mv** is used to move files directories and unlike **cp** which requires altering behavior to copy directories

**rm** can be used to remove a file

finally i leave you with a [link](https://ryanstutorials.net/linuxtutorial/cheatsheet.php) to a cheatsheet for linux commands
