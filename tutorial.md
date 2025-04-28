## *Shell Scripting Tutorial*

#### Introduction

Shelling Scripting is essential for task automation and running shell commands as a single unit. It is basically a collection of shell commands in a file. A Shell Script is a file with a ".sh" extension and can be run using shell compilers such as bash, zsh etc.
It can also use loops and conditionals but the syntax is quite different from any High Level Language.
Imaging you're on a server or an embedded system where there's no GUI, just a simple shell terminal, so you can't access download any setup using GUI. Here's when Shell scripting comes into play. You can install tools and navigate through the directories using these scripts.

#### Navigating FIles

To print the path of the directory you're currently in, use the `pwd` command. The output will look like:
```
/home/username/Desktop/MEDS_Training
```

Using the `ls` command, you can get a list of all the visible files and subdirectories in a directory. `ls -a` can be used to print the hidden files and subdirectories as well.

In order to navigate through directories, use the `cd` command. To go into a subdirectory use:
```
cd path/directory_name
```
To move back a directory(parent directory), use `cd ..` command.
Just for the information, `..` means parent directory, `.` means current directory and `*` means all.

#### File Handling/Manipulation

###### Copying a File
You can also copy and paste using shell as well. In order to copy a file from one subdirectory to another, use the `cp` command:
```
cp source-path/file.ext dest-path/file.ext
```
To copy from/to the current directory, use `.` instead of the path or drop the whole `./` .

###### Moving a File
To move a file from one path to another, use the `mv` command:
```
mv source-path/file.ext dest-path/file.ext
```

###### Renaming a File
Though there isn't an already defined command for renaming, you can use the `mv` command to rename a file by keeping the source and dest path the same but changing the file name:
```
mv ./file.ext ./new_filename.ext
```

###### Create a File

Use the `touch` command to create a file:
```
touch path/filename.ext
```
###### Creating a Directory

You can use the `mkdir` command to create an empty directory:
```
mkdir path/directory_name
```

###### Removing a Directory

You can remove an empty directory using the `rmdir` command, ONLY if it's empty:
```
rmdir path-of-directory/name
```
If the directory is not empty, you can use the `rm` command recursively using the `-r` (means recursive) option, and if required, use the `-f` (means forced) option along with it.
`rf` (means forced recursive):
```
rm -rf path/directory_name
```

#### Displaying Contents
You can directlty manipulate a file without opening it using some basic shell commands like `cat` etc.

###### Printing a File
Without opening a file, you can print its contents using the `cat` command:
```
cat path/filename.ext
```

###### Printing the Start/End
Using the `head` command, you can print the first 10 lines (by default) of any file:
```
head path/file.ext
```
Using the `-n *lines*` option, proceeding with the number of lines you want to print (10 by default), you can print any desired lines from the start of a file:
```
head -n 4 path/file.ext 
```
`tail` command is used to print the last 10 lines of a file. `-n *lines*` is used to choose the number of lines to display:
```
tail -n 4 path/file.ext
```

#### Usage of `grep` command
`grep` is used to search for certain patterns in a file and then copy and paste those certain lines depending upon the result.

###### Seaching a Pattern
`grep`, when used, returns the whole line which includes the pattern provided to it. The syntax is:
```
grep "pattern" path/filename.ext
```
If there are more than one files to search, simply provide their paths and names along side the first one:
```
grep "pattern" path/file1.ext path/file2.ext
```
In order to search a pattern in all the files with the same extension:
```
grep "pattern" *.ext
```
Just like mentioned above, * represents all the file in the current directory.

###### Copying and Pasting Lines using `grep`
`grep` can also be used to copy or overwrite specific lines with the provided pattern
```
grep "pattern" path/src_file.ext > path/dest_file.ext
```
This command is used to overwrite the file content with only the lines containing the pattern in src_file.ext
Where as, if you just want to append those those in the dest_file.ext, use `>>` instead of `>`:
```
grep "pattern" path/src_file.ext >> path/dest_file.ext
```

#### Bash Scripting Basics
You can also write all the shell commands and make a `.sh` file to run these commands all at once. This kind of file is called a script and it may also include loops, variables as well as conditionals but the syntax is a little different from High Level Languages

###### Compilers for Bash
There are many compilers for shell scripts. The most popular ones are `bash` and `zsh`. When running a script, you'll either have to call the compiler name before writing the script file name:
```
bash script.sh
```
Or, for zsh:
```
zsh script.sh
```

Or you can also write a comment `#!/bin/bash` at the start of every bash script to tell the shell that when you run this script, run it using the bash compiler in bin directory.

###### Variables in Shell Scripts
Just like in other languages, you can define variables in bash and use them as well. Variable definition is like this in bash:
```
var1=4
var2=7
```
Keep in mind, no spaces should be in between the assignment operator, the name and the data.
To call a varible we use a `$` before the name like this:
```
echo $var1
echo $var2
```
Note: `echo` is used to print something on the terminal written after it.
When we use want to perform any arithematic operation on the variables or numbers directly, use double parantheses and a `$` at the start but not with the variable names:
```
echo $((var1+var2))
```
This prints 12, where:
```
echo $((1-2))
```
This prints -1.

###### Operators
There are many types of operators in bash, logical, arithematic and even for file verification operations
We'll cover some of these operators and some references will be provided if someone wants to further study these operators
 - ###### Logical Operators
    | Operator |        Use                       |
    |----------|----------------------------------|
    | -eq      | Equal To                         |
    | -ne      | Not Equal To                     |
    | -lt      | Less Than                        |
    | -gt      | Greater Than                     |
    | -ge      | Greater Than or Equal            |
 - ###### File Test Operators
    | Operator |        Use                       |
    |----------|----------------------------------|
    | -e       | Checks if file Exists            |

The References for the operators are given below:
 - [Geeks For Geeks](https://www.geeksforgeeks.org/basic-operators-in-shell-scripting/)
 - [Linux HandBook](https://linuxhandbook.com/bash-test-operators/)

###### Conditionals
If and else statements are also used in Scripting. The syntax is:
```
if [ condition ]
then
    block-of-bash-statements
elif [ condition ]; then
    block-of-bash-statements
else
    block-of-bash-statements
fi
```
Keep in mind, if then is to be added on the same line as the if statement, `;` must be used. Also, a conditional block always ends with `fi`.

###### Loops in Shell Scripts
Just like in any language, there are two basic loops in bash. `for` and `while` loops.

###### `for` Loops
`for` loops can be written using 2 types of syntax:
 - ***Syntax 1***
    ```
    for ((i=0;i<5;i++))
    do
        block-of-statements
    done
    ```
 - ***Syntax 2***
    ```
    for i in {0..4}
    do
        block-of-statements
    done
    ```
    Instead of `{0..4}`, can also make it iterate over an array by passing `0,1,2,3,4` instead.

###### `while` Loops
while loop syntax is also similar to other languages:
```
while [ condition ]
do
    block-of-statements
done
```
Or to iterate a number of times:
```
counter=0
while [ $counter -le 5 ]; do
    block-of-statements
    counter=$((counter+1))
done
```

#### References
You can also use the following references for help regarding any command or use `--help` after any command to see what it does and its options

   - [MicroSoft's Tutorial](https://learn.microsoft.com/en-us/training/paths/shell/)
   - [MIT Link 1](https://missing.csail.mit.edu/2020/course-shell/)
   - [MIT Link 2](https://missing.csail.mit.edu/2020/shell-tools/)







