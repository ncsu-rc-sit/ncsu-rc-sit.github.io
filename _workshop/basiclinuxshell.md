---
layout: post
title: Basic Linux Commands
feature-img: "assets/img/background-color.png"
date: 26 November 2024
---
## Introduction
Linux commands are issued to a computer program called
`shell`. The shell enables us to send commands to the
computer and receive output. It is also referred to as
the terminal or command line interface~(CLI). Some
computers include a default Unix Shell program. If not
natively present, a program called Linux/Unix emulator
can be installed to access a Unix Shell on a server.

In addition, the command line is often the easiest way to interact
with remote machines and supercomputers. **Familiarity with the shell
is near essential to run a variety of specialized tools and resources
including high-performance computing systems**. As clusters and cloud
computing systems become more popular for scientific data crunching,
being able to interact with the shell is becoming a necessary skill.
We can build on the command-line skills covered here to tackle a wide
range of scientific questions and computational challenges.

This workshop is designed on the model developed by the [Software and Data
Carpentry](https://carpentries.org/workshops/). The material on this page is
part from the [Software Carpentry Lessons](https://software-carpentry.org/lessons/)

To continue with the learning process, we encourage participants to follow the
steps below for setup.
* [Setup](#TheSetup)
* [Windows](#Windows)
* [macOS](#macOS)
* [Linux](#Linux)

<a name="TheSetup"></a>
## Setup
Download [data-shell.zip](http://swcarpentry.github.io/
shell-novice/data/data-shell.zip) and move the file to
your Desktop. Unzip/extract the file. You should have a
new folder called `data-shell` on your Desktop.
Open a terminal. If you’re not sure how to open a
terminal in your operating system, see the instructions
below. In the terminal type `cd` then press the 'Return'
key. This step will make sure you start with your home
folder as your working directory. Later on, you will
find out how to access the data files in this folder.

<a name="Windows"></a>
### Windows
Computers with Windows operating systems(OS) older than
Windows 10 do not have the Bash shell installed by default.
If you have a Windows OS older than Windows 10, we encourage
you to use an emulator included in Git for Windows, which
gives you access to both Bash shell commands and Git. Once
installed, you can open a terminal by running the program Git
Bash from the Windows start menu.

Additionally, you can run Bash commands from a remote
computer or server that already has a Unix Shell. This
can usually be done through a Secure Shell (SSH) client.
One such client available for free for Windows computers
is PuTTY. See the **reference** below for information on
installing and using PuTTY, using the Windows 10 command-line
tool, or installing and using a Unix/Linux emulator.

**Reference**
  * [Git for Windows](https://gitforwindows.org/) - Recommended

**For advanced users, you may choose one of the following alternatives**:
  * [Install the Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
  * [Using a Unix/Linux emulator (Cygwin) or Secure Shell (SSH) client (Putty)](http://faculty.smu.edu/reynolds/unixtut/windows.html)
Please note that commands in the Windows Subsystem for Linux or Cygwin may differ slightly from those shown in the lesson or presented in the workshop.

<a name="macOS"></a>
### macOS
For a Mac computer running macOS Mojave or earlier
releases, the default Unix Shell is Bash. For a Mac
computer running macOS Catalina or later releases,
the default Unix Shell is `Zsh`. Your default shell is
available via the Terminal program within your Utilities
folder. To open Terminal, try one or both of the following:
  * In Finder, select the Go menu, then select Utilities. Locate Terminal in the Utilities folder and open it.
  * Use the Mac `Spotlight` computer search function. Search for: `Terminal` and press `Return`.

To check if your machine is set up to use something other than Bash, type `echo $SHELL` in your terminal
window.
           
If your machine uses something other than Bash, you can run it by opening a terminal and typing
`bash`.

  * [How to Use Terminal on a Mac](http://www.macworld.co.uk/feature/mac-software/how-use-terminal-on-mac-3608274/)

<a name="Linux"></a>
### Linux
The default Unix Shell for Linux operating systems is
usually Bash. On most versions of Linux, it is accessible
by running the [Gnome Terminal](https://help.gnome.org/users/gnome-terminal/stable/)
or [KDE Konsole](https://konsole.kde.org/) or [xterm](https://en.wikipedia.org/wiki/Xterm),
which can be found via the applications menu or the
search bar. If your machine is set up to use something
other than Bash, you can run it by opening a terminal
and typing bash.

This workshop will not make you an expert but will provide you with a good
enough foundation for a personal exploration the Unix shell. The shell has
a very rich echo system of commands but we will only touch on those deemed
essential for scientific computing. The lesson is structured as follows:

1. [Introducing the Shell](#TheShell)
2. [Navigating Files and Directories](#FilesDirectories)
3. [Pipes and Filters](#PipesFilters)
4. [Finding Things](#FindThings)

<a name="TheShell"></a>
## Introducing the Shell    
Using the shell will take some effort and some time to learn.
While a GUI presents you with choices to select, CLI choices
are not automatically presented to you. Unlike a spoken language,
a small number of “words” (i.e. commands) gets you a long way,
and we’ll cover those essential few today.

The grammar of a shell allows you to combine existing tools into
powerful pipelines and handle large volumes of data automatically.
Sequences of commands can be written into a script, improving the
reproducibility of workflows.

When the shell is first opened, you are presented with a prompt,
indicating that the shell is waiting for input.
```
Bash
$  
```
The shell typically uses `$` as the prompt, but may use a different symbol.
So let’s try our first command, `ls` which is short for listing. This command
will list the contents of the current directory:

```
Bash
$ ls  
```
```
Output

$ Desktop   Downloads  Movies  Pictures
  Document  Library    Music   Public   
```

*If the shell can't find a program whose name is the command typed, it will print an error message such as:
```
Bash
$ ks  
```
```
Output

$ ks: command not found
```
This might happen if the command was mis-typed or if the program corresponding to that command is not installed.

**A Typical Problem**
A marine biologist, has just returned from a six-month survey of the [North Pacific Gyre](https://en.wikipedia.org/wiki/North_Pacific_Gyre), where she has been sampling gelatinous marine life in the [Great Pacific Garbage Patch](https://en.wikipedia.org/wiki/Great_Pacific_garbage_patch). She has *1520* samples that she’s run through an assay machine to
measure the relative abundance of *300* proteins. She needs to run these 1520 files through an imaginary program called
`goostats` she inherited. On top of this huge task, she has to write up results by the end of the month so her paper
can appear in a special issue of `Aquatic Goo Letters`.

The bad news is that if she has to run `goostats` by hand using a GUI, she’ll have to select and open a file *1520*
times. If `goostats` takes *30* seconds to run each file, the whole process will take more than *12* hours of the
scientist’s attention. With the shell, she can instead assign her computer this mundane task while she focuses her
attention on writing her paper.

The next few lessons will explore the ways the task can be achieved. More specifically, they explain how command
shell can be used to run the `goostats` program, using loops to automate the repetitive steps of entering file names,
so that her computer can work while she writes her paper.

As a bonus, once the processing pipeline has been put together, it can be used again whenever more data is collected.


<a name="FilesDirectories"></a>
## Navigating Files and Directories

The part of the operating system responsible for managing files and directories is called the **file system**.
It is organized in multiple layers. The top most layer is the root directory. When you remotely login to a
computer for the first time, you get on the home directory. Every user account on a server (High Performance Computer)
has a home directory.

<img src="/assets/img/tutorialsimages/GoogleDrive/img1.png", Alt = "Examples of a file system" >

The forward slash character `/` does two things:
  * When it appears at the front of a file or directory name, it refers to the root directory.
  * When it appears inside a path, it’s just a separator.

The root directory `/` has `/bin`, `/data`, `/Users`, and `/tmp` directories. The `/Users` directory in turn
has the `/Users/Sarah`, `/Users/Jacob` and `/Users/Nelle` directories. The path from the root directory
to any targeted file or directory is called the **absolute path**. `/Users/Sarah`, `/Users/Jacob` and `/Users/Nelle`
are the abasolute paths to Sarah's, Jacob's, and Nelle's home directories.

Download the `data-shell.zip` from the setup section on to your destop. Start the terminal on your computer.

Use the command below to determine your home directory
```
Bash
$ echo $HOME  
```
```
Output
$ /Users/Jacob
```
Determine your current working directory (data-shell)
```
Bash
$ pwd  
```
```
Output
$ /Users/Jacob/Desktop/data-shell
```
List the content of your current working directory with `ls`
```
Bash
$ ls
```
```
Output
$ creatures          molecules          notes.txt           solar.pdf
  data               north-pacific-gyre pizza.cfg           writing
```
`ls` prints the names of the files and directories in the current directory. We can make its output more
comprehensible by using the *-F* option (also known as a switch or a flag) , which tells `ls` to classify
the output by adding a marker to file and directory names to indicate what they are:
  * a trailing / indicates that this is a directory
  * @ indicates a link
  * \* indicates an executable

Depending on your default options, the shell might also use colors to indicate whether each entry is a file
or directory. 
```
Bash
$ ls -F 
```
```
Output
$ creatures/          molecules/          notes.txt           solar.pdf
  data/               north-pacific-gyre/ pizza.cfg           writing/
```
### Syntax of a shell command
Consider a general example of a command, which we will dissect into its component parts: 
```
Bash
$ ls -F /
```
```
Output
Applications/ System/       bin/          etc@          private/      usr/
Library/      Users/        cores/        home@         sbin/         var@
Network@      Volumes/      dev/          opt/          tmp@
```

`ls` is the command, with an option `-F` and an argument `/`.  We’ve already encountered options
(also called switches or flags) which either start with a single dash (-) or two dashes (--), and
they change the behaviour of a command. Arguments tell the command what to operate on (e.g. files and directories).
Sometimes options and arguments are referred to as parameters. A command can be called with more than one option
and more than one argument, but doesn’t always require an argument or an option.

Each part is separated by spaces: if you omit the space between `ls` and `-F` the shell will look for a command
called `ls-F`, which doesn’t exist. Also, capitalization can be important. For example, `ls -s` will display the
size of files and directories alongside the names, while `ls -S` will sort the files and directories by size, as
shown below:

```
Bash
$ ls -s /Users/Jacob/Desktop/data-shell/data/
total 208
  8 amino-acids.txt    0 elements/         24 planets.txt
  0 animal-counts/     8 morse.txt          8 salmon.txt
  8 animals.txt        0 pdb/             152 sunspot.txt
```
and
```
Bash
$ ls -S /Users/Jacob/Desktop/data-shell/data/
sunspot.txt      elements/        morse.txt        animals.txt      salmon.txt
planets.txt      pdb/             amino-acids.txt  animal-counts/

```
### Getting Help
There are two common ways to find out how to use a command and what options it accepts:
  1. We can pass a` --help` option to the command, such as
  ```
  Bash
  $ ls --help
  ```
  ```
  Output
  ls: illegal option -- -
  usage: ls [-@ABCFGHLOPRSTUWabcdefghiklmnopqrstuwx1%] [file ...]
  ```
 2. We can read its manual with `man`, such as
  ```
  Bash
  $ man ls
  ```   
  ```  
  Output     
   LS(1)                     BSD General Commands Manual                    LS(1)
   NAME
      ls -- list directory contents
   SYNOPSIS
      ls [-ABCFGHLOPRSTUW@abcdefghiklmnopqrstuwx1%] [file ...]
   DESCRIPTION
      For each operand that names a file of a type other than directory, ls displays
      its name as well as any requested, associated information.  For each operand that
      names a file of type directory, ls displays the names of files contained within
      that directory, as well as any requested, associated information.
    
      If no operands are given, the contents of the current directory are displayed.
      If more than one operand is given, non-directory operands are displayed first;
      directory and non-directory operands are sorted separately and in lexicographical
      order.

      The following options are available:

      -@      Display extended attribute keys and sizes in long (-l) output.
   :
  ```
  
Continue to push on the space bar of your computer to scroll down the `ls` manual.
Sometimes at the bottom of the manual, you see some examples of how to use the command.
Push the `q` key to exit the `man` page.

If you try to use an option (flag) that is not supported, `ls` and other commands will usually print
an error message similar to:

```
Bash
$ ls -j
```
```
Output
ls: illegal option -- j
usage: ls [-@ABCFGHLOPRSTUWabcdefghiklmnopqrstuwx1%] [file ...]
```

### Exploring Directories

We can look at the content of `data-shell` by passing the directory name to ls
```
Bash
$ ls -F /Users/Jacob/data-shell
```
```
Output
creatures/          molecules/          notes.txt           solar.pdf
data/               north-pacific-gyre/ pizza.cfg           writing/
```
We can use the *change directory* `cd` command to move from one directory to another.
This is akin to double clicking on a directory in a GUI environment. The command below
moves from `data-shell` directory to its subdirectory `data`.
```
Bash
$ cd data
```
Use `pwd` command to confirm your location
```
Bash
$ pwd
```
```
Output
/Users/Jacob/Desktop/data-shell/data

```
So far, 'cd' only sees sub-directories inside your current directory. There are different
ways to see directories above your current location. This is done using a shortcut in the
shell to move up one directory level that looks like this:

```
Bash
$ cd ..
```
`pwd` can then be used to verify our location

```
Bash
$ pwd
```
```
Output
/Users/Jacob/Desktop/data-shell

```
We can see that `cd ..` takes us back to `data-shell` directory.
`..` is a special directory that is always present in all directories. To see
this special directory and other hidden files in a directory, we add `-a` option to the
`ls` command.
```
Bash
$ ls -a -F
```
```
Output
./                  creatures/          north-pacific-gyre/ solar.pdf
../                 data/               notes.txt           writing/
.bash_profile       molecules/          pizza.cfg
```
`-a` stands for ‘show all’. It forces `ls` to show us file and directory names that begin with `.`,
such as `..` (which, if we’re in /Users/Jacob, refers to the /Users directory) As you can see,
it also displays another special directory that’s just called `.`, which means 'the current working directory'. 

**Note that** in most command line tools, multiple options can be combined with a single `-` and no
spaces between the options, `ls -F -a` is equivalent to `ls -Fa`.

**Important Shortcuts**   
`~` (tilde) at the start of a path means “the current user’s home directory”. For example, if Jacob’s
home directory is /Users/Jacob, then `~/Deskstop/data-shell/data` is equivalent to
`/Users/Jacob/Desktop/data-shell/data`. *This only works if `~` is the first character in the path*

`-` (dash) character istranslated by `cd` to mean *previous directory* I was in, which is faster than
having to remember, then type, the full path. This is a very efficient way of moving back and forth
between directories.

**Note that** `cd ..` takes you up, one level while `cd -` takes you back where you were previousely.
You can think of it as the Last channel button on a TV remote.

### Absolute and Relative Paths
An *absolute path* is defined as specifying the location of a file or directory from the root directory(/).
`/Users/Jacob/Desktop/data-shell/data` is the absolute path to the `data` directory. Use `cd` only or `cd ~`
to go back to your home directory. From your home directory, go back to the `data` directory using its absolute
path
```
Bash
$ cd
```
```
Bash
$ pwd
```
```
Output
/Users/Jacob/
```
```
Bash
$ cd /Users/Jacob/Desktop/data-shell/data
```
```
Bash
$ pwd
```
```
Output
/Users/Jacob/Desktop/data-shell/data
```
*Relative path* is defined as the path related to the present working directly(pwd).
Use the *relative path* to get to the `Desktop` directory and back to the `data` directory
```
Bash
$ cd ../..
```
```
Bash
$ pwd
```
```
Output
/Users/Jacob/Desktop
```
Now go back to the `data` directory
```
Bash
$ cd data-shell/data
```
```
Bash
$ pwd
```
```
Output
/Users/Jacob/Desktop/data-shell/data
```
The relative path from `data` to `Desktop` directory is `../..` and the relative path
back to `data` from `Desktop` directory is `data-shell/data`.

### Copying and Making Copies of Files and Directories

**Questions**  
* How can I create, copy, and delete files and directories?    
* How can I edit files?

**Objectives**      
* Create a directory hierarchy that matches a given diagram.
* Create files in that hierarchy using an editor or by copying and renaming existing files.
* Delete, copy and move specified files and/or directories.

We will now explore how to create files and directories. Let’s create a new
directory called `thesis` using the command `mkdir thesis`:
```
Bash
$ mkdir thesis
```
The `-p` option allows `mkdir` to create a directory with any number of nested
subdirectories in a single operation:
```
Bash
$ mkdir -p thesis/chapter_1/section_1/subsection_1
```
The `-R` option to the `ls` command will list all nested subdirectories
wtihin a directory. Let’s use `ls -FR` to recursively list the new directory
hierarchy we just created beneath the `thesis` directory:
```
Bash
$ ls -FR thesis
```
```
Output
     chapter_1/

     thesis/chapter_1:
     section_1/

     thesis/chapter_1/section_1:
     subsection_1/
```
**Good Names for Files and Directories**

Complicated names of files and directories can make your life painful when
working on the command line. A few useful tips for the names of your files:

1. *Don’t use spaces.* Spaces are used to separate arguments on the command
line. You can use `-` or `_` instead (e.g. north-pacific-gyre/ rather than north pacific gyre/).         

2. *Don’t begin the name with `-` (dash).* Commands treat names starting with - as options.       

3. *Stick with letters, numbers, `.` (period or `full stop`), - (dash) and `_`
(underscore).* Many other characters have special meanings on the command
line. Some can cause your command to not work as expected and can even result
in data loss.     

If you need to refer to names of files or directories that have spaces or
other special characters, you should surround the name in quotes ("").

**Create a text file**
 We can use the `touch` command to create an empty text file.
 A text editor could also be used. There are many text editors of which
 [`Emacs`](https://www.emacswiki.org/), [`vim`](https://www.vim.org/),
 and [`nano`](https://www.nano-editor.org/) are three of the most used. `nano`
 is the simplest and will be used for editing files.

Create `draft.txt` file with the command  `nano draft.txt`. Once the file is
Open, type a few words and press `Ctrl+O` (press the Ctrl or Control key and,
while holding it down, press the O key) to write our data to disk (we’ll be
asked what file we want to save this to: press `Return` to accept the
suggested default of draft.txt).

**Moving Files and Directories**
```
Bash
$ cd ~/Desktop/data-shell/
```
In `thesis` directory is a file `draft.txt` which isn’t a particularly
informative name, so let’s change the file’s name using `mv`, which is
short for `move`:

```
Bash
$ mv thesis/draft.txt thesis/quotes.txt
```
Use the `ls` command to verify if `quotes.txt` is in the directory. The file
could be moved into the current directory represented by `.`:
```
Bash
$ mv thesis/quotes.txt .
```
**Copying Files and Directories**                    
The `cp` command works very much like `mv`, except it copies a file instead
of moving it.         
```
Bash
$ cp quotes.txt thesis/quotations.txt
$ ls quotes.txt thesis/quotations.txt
```
We can also copy a directory and all its contents by using the recursive
option `-r`, e.g. to back up a directory:

```
Bash
$ cp -r thesis thesis_backup
```

**Removing Files and Directories**           
Returning to the `data-shell` directory, let’s tidy up this directory by
removing the `quotes.txt` file we created. The Unix command we’ll use for
this is `rm` (short for ‘remove’):
```
Bash
$ rm quotes.txt
```
**Question**: What happens when we execute `rm -i thesis_backup/quotations.txt`? Why would we want this protection when using `rm`?

`rm` can remove a directory and all its contents if we use the recursive
option `-r`, and it will do so without any confirmation prompts:
```
Bash
$ rm -r thesis
```
<span style="color:red">Given that there is no way to retrieve files deleted using the shell, `rm -r` should be used with great caution (you might consider adding the interactive option `rm -r -i`)</span>.

**Using wildcards for accessing multiple files at once**

`*` is a **wildcard**, which matches zero or more characters. Let’s consider
the `data-shell/molecules` directory: `*.pdb` matches all the files ending
in `.pdb`
```
Bash
$ ls ~/Desktop/data-shell/molecules/*.pdb
```
```
Output
     ~/Desktop/data-shell/molecules/cubane.pdb
     ~/Desktop/data-shell/molecules/ethane.pdb
     ~/Desktop/data-shell/molecules/methane.pdb
     ~/Desktop/data-shell/molecules/octane.pdb
     ~/Desktop/data-shell/molecules/pentane.pdb
     ~/Desktop/data-shell/molecules/propane.pdb
```
 `?` is also a wildcard, but it matches exactly one character. So
 `?ethane.pdb` would match `methane.pdb` whereas `*ethane.pdb` matches
 both `ethane.pdb`, and `methane.pdb`.

Wildcards can be used in combination with each other e.g. `???ane.pdb` matches
three characters followed by `ane.pdb`, giving `cubane.pdb`, `ethane.pdb`, `octane.pdb`.






<a name="PipesFilters"></a>
## Pipes and Filters

**Questions**    
* How can I combine existing commands to do new things?

**Objectives**       
* Redirect a command’s output to a file.
* Process a file instead of keyboard input using redirection.
* Construct command pipelines with two or more stages.

We’ll start with the directory called `data-shell/molecules` that contains six
files describing some simple organic molecules. The .pdb extension indicates
that these files are in Protein Data Bank format, a simple text format that
specifies the type and position of each atom in the molecule.

```
Bash
$ cd ~/Desktop/data-shell/molecules
```
*wc* is the `word count` command: it counts the number of lines, words, and
characters in files (from left to right, in that order).

If we run the command `wc \*.pdb`, the \* in \*.pdb matches zero or more
characters, so the shell turns \*.pdb into a list of all .pdb files in the
current directory:
```
Bash
$ wc *.pdb
```
```
Output
 20     156    1158 cubane.pdb
 12      84     622 ethane.pdb
  9      57     422 methane.pdb
 30     246    1828 octane.pdb
 21     165    1226 pentane.pdb
 15     111     825 propane.pdb
107     819    6081 total
```
The `-m`, `-w` and `-l` options can also be used with the wc command, to show
only the number of characters, words or the number of lines in the files.
```
Bash
$ wc -l *.pdb
```
```
Output
 20 cubane.pdb
 12 ethane.pdb
  9 methane.pdb
 30 octane.pdb
 21 pentane.pdb
 15 propane.pdb
107 total
```
We can redirect our output into a file say "lenghts.txt", "characters.txt" or
"words.txt"
```
Bash
$ wc -l *.pdb > lenghts.txt
```
```
Bash
$ wc -m *.pdb > characters.txt
```
```
Bash
$ wc -w *.pdb > words.txt
```
We can merge the three files and direct the output into a new file "lwc.txt":
```
Bash
$ cat lenghts.txt words.txt characters.txt > lwc.txt
```
By default `sort` do an alphanumerical reordering and the `-n` option
specifies that the sort is numerical instead:
```
Bash
$ sort lwc.txt
```
The output of the previous command is long but we can choose to print only
the the first 5 lines using `head` command or the last 5 lines using the
`tail` command:
```
Bash
$ sort lwc.txt | head -n 5
```
```
Output
 9 methane.pdb
12 ethane.pdb
15 propane.pdb
20 cubane.pdb
21 pentane.pdb
```
```
Bash
$ sort lwc.txt | head -n 5
```
```
Output
 825 propane.pdb
1158 cubane.pdb
1226 pentane.pdb
1828 octane.pdb
6081 total
```
We can show the efficiency of piping and the `cut` command.
A file called animals.txt (in the data-shell/data folder) contains the
following data:
```
Bash
$ cat ~/Desktop/data-shell/data/animal.txt
```
The `cut` command, the delimiter `-d ,` and the field `-f 2` returns the
animal's names
```
Bash
$ cut -d , -f 2 animals.txt
```
```
Output
deer
rabbit
raccoon
rabbit
deer
fox
rabbit
bear
```
The contain of the files is split at the comma into 2 fields and the second
field is returned.

**Check for errors**

Nelle has run her samples through the assay machines and created 17 files in
the north-pacific-gyre/2012-07-03 directory. As a quick check, starting from
her home directory, Nelle types:
```
Bash
$ cd north-pacific-gyre/2012-07-03/
$ wc -l *.txt
```
```
Output
    300 NENE01729A.txt
    300 NENE01729B.txt
    300 NENE01736A.txt
    300 NENE01751A.txt
    300 NENE01751B.txt
    300 NENE01812A.txt
    300 NENE01843A.txt
    ... ...     
```
We can sort the output to look for inconsistencies
```
Bash
$ wc -l *.txt | sort -n | head -n 5
```
```
Output
     240 NENE02018B.txt
     300 NENE01729A.txt
     300 NENE01729B.txt
     300 NENE01736A.txt
     300 NENE01751A.txt
```
We can see that one of the files has 60 fewer lines.

<a name="FindThings"></a>
## Finding Things

**Questions**    
 * How can I find files?   
 * How can I find things in files?

**Objectives**       
 * Use *grep* to select lines from text files that match simple patterns.    
 * Use find to find files and directories whose names match simple patterns.

Unix programmers often use the word `grep`. `grep` is a contraction of
`global/regular expression/print`, a common sequence of operations in early
Unix text editors. It is also the name of a very useful command-line program.  
`grep` finds and prints lines in files that match a pattern. For this set of examples, we’re going to be working in the writing subdirectory:
```
Bash
$ cd
$ cd ~/Desktop/data-shell/writing
$ cat haiku.txt
```
Let's find lines that contain word not :
```
Bash
$ grep not haiku.txt
```
By default, grep searches for a pattern in a case-sensitive way. In addition,
the search pattern we have selected does not have to form a complete word, as
we will see in the next example. Let’s search for the pattern: ‘The’.

```
Bash
grep The haiku.txt
```
This time, two lines that include the letters `The` are outputted, one of
which contained our search pattern within a larger word, ‘Thesis’. To restrict
matches to lines containing the word `The` on its own, we can give grep with
the *-w* option. This will limit matches to word boundaries.

```
Bash
grep -w The haiku.txt
```
Sometimes we don’t want to search for a single word, but a phrase. This is
also easy to do with grep by putting the phrase in quotes.

```
Bash
$ grep -w "is not" haiku.txt
```
Another useful option is *-n*, which numbers the lines that match:
```
Bash
$ grep -n "it" haiku.txt
```
Now, we want to use the option *-v* to invert our search, i.e., we want to
output the lines that do not contain the word ‘the’.
```
Bash
$ grep -nwv "the" haiku.txt
```
While grep finds lines in files, the find command finds files themselves.
Again, it has a lot of options; we will show how the simplest ones work.

For our first command, let’s run `find .` (remember to run this command from
the data-shell/writing folder).

```
Bash
$ find .
```
The first option in our list is `-type d` that means things are directories.

```
Bash
$ find . -type d
```
Notice that the objects `find` finds are not listed in any particular order.
If we change `-type d` to `-type f`, we get a listing of all the files instead:
```
Bash
$ find . -type f
```
Now let's try matching by name

```
Bash
$ find . -name *.txt
```
```
Output
$ ./haiku.txt
```
We expected it to find all the text files, but it only prints out
`./haiku.txt`. The problem is that the shell expands wildcard characters
like \* before commands run. Since \*.txt in the current directory expands
to haiku.txt.

To get what we want, let’s do what we did with grep: put \*.txt in quotes to
prevent the shell from expanding the \* wildcard. This way, `find` actually
gets the pattern \*.txt, not the expanded filename haiku.txt:

```
Bash
$ find . -name "*.txt"
```
The command line’s power lies in combining tools. We’ve seen how to do that
with pipes; let’s look at another technique. As we just saw,
`find . -name "*.txt"` gives us a list of all text files in or below the
current directory. How can we combine that with `wc -l` to count the lines in
all those files?

The simplest way is to put the find command inside $():
```
Bash
$ wc -l $(find . -name "*.txt")
```
```
Output
11 ./haiku.txt
300 ./data/two.txt
21022 ./data/LittleWomen.txt
70 ./data/one.txt
21403 total
```
