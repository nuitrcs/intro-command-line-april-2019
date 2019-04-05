# Command Line Session 1

---
This is the material we'll cover during the second part of the workshop (Day 2 morning).  We may deviate a little, but we'll work from this.

We're changing gears and working exclusively in Command line. 

Goal for this morning is to get accustomed to command line environment and be able to find your way, run the script and few more fun staff at the end of the morning.

Questions for the first part:
- "What is a command shell and why would I use one?"
Objectives:
- "Explain how the shell relates to the keyboard, the screen, the operating system, and users' programs."
- "Explain when and why command-line interfaces should be used instead of graphical interfaces."
---

## Prerequisites
You need to download some files to follow this lesson:

1. Download [data-shell.zip](https://github.com/nuitrcs/commandlineworkshop/blob/master/shell-novice-data.zip?raw=true) and move the file to your Desktop.
2. Unzip/extract the file (ask your instructor if you need help with this step). You should end up with a new folder called **data-shell** on your Desktop.
3. Open a terminal and type `cd`, then press the Enter key. That last step will make sure you start with your home folder as your working directory.

In the lesson, you will find out how to access the data in this folder.  

> ## Where to type commands: How to open a new shell
> The shell is a program that enables us to send commands to the computer and receive output. It is also referred to as the terminal or command line.
>
> Some computers include a default Unix Shell program. 
> The steps below describe some methods for identifying and opening a Unix Shell program if you already have one installed. 
> There are also options for identifying and downloading a Unix Shell program, a Linux/UNIX emulator, or a program to access a Unix Shell on a server. 
>
> If none of the options below address your circumstances, try an online search for: Unix shell [your computer model] [your operating system].
>
> ### Linux
> The default Unix Shell for Linux operating systems is usually Bash.
> On most versions of Linux, it is accessible by running the [(Gnome) Terminal](https://help.gnome.org/users/gnome-terminal/stable/)
> or [(KDE) Konsole](https://konsole.kde.org/)
> or [xterm](https://en.wikipedia.org/wiki/Xterm),
> which can be found via the applications menu or the search bar.
> If your machine is set up to use something other than bash, you can run it by opening a terminal and typing `bash`.
>
> ### Mac OS
> For a Mac computer, the default Unix Shell is Bash,
> and it is available via the Terminal Utilities program within your Applications folder.
>
> To open Terminal, try one or both of the following:
> * Go to your Applications. Within Applications, open the Utilities folder. Locate Terminal in the Utilities folder and open it.
> * Use the Mac ‘Spotlight’ computer search function. Search for: `Terminal` and press <kbd>Return</kbd>.
>
> #### Reference 
> [How to Use Terminal on a Mac](http://www.macworld.co.uk/feature/mac-software/how-use-terminal-on-mac-3608274/)
>
> ### Windows
> Computers with Windows operating systems do not automatically have a Unix Shell program installed.
> In this lesson, we encourage you to use an emulator included in Git for Windows, 
> which gives you access to both Bash shell commands and Git. 
> If you are attending a Software Carpentry workshop session, it is likely you have already received instructions on how to install Git for Windows.
>
> Once installed, you can open a terminal by running the program Git Bash from the Windows start menu.
>
> Other solutions are available for running Bash commands on Windows. 
> There is now a Bash shell command-line tool available for Windows 10. 
> Additionally, you can run Bash commands on a remote computer or server that already has a Unix Shell, from your Windows machine. 
> This can usually be done through a Secure Shell (SSH) client. 
> One such client available for free for Windows computers is PuTTY. 
> See the reference below for information on installing and using PuTTY, 
> using the Windows 10 command-line tool, or installing and using a Unix/Linux emulator.
>
> #### Reference
> * [Git for Windows](https://git-for-windows.github.io/)
> * [Install the Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
> * [Using a Unix/Linux emulator (Cygwin) or Secure Shell (SSH) client (Putty)](http://faculty.smu.edu/reynolds/unixtut/windows.html)

## Background
At a high level, computers do four things:

-   run programs
-   store data
-   communicate with each other, and
-   interact with us


They can do the last of these in many different ways,
including through a keyboard and mouse, touch screen interfaces, or using speech recognition systems.
While touch and voice interfaces are becoming more commonplace, most interaction is still
done using traditional screens, mice, touchpads and keyboards.

We are all familiar with **graphical user interfaces** (GUI): windows, icons and pointers.
They are easy to learn and fantastic for simple tasks where a vocabulary consisting of
"click" translates easily into "do the thing I want". But this magic relies on 
wanting a simple set of things, and having programs that can do exactly those things.

If you wish to do complex, purpose-specific things it helps to have a richer means
of expressing your instructions to the computer. It doesn't need to be complicated or
difficult, just a vocabulary of commands and a simple grammar for using them.

This is what the shell provides - a simple language and a **command-line interface** 
to use it through. 

The heart of a command-line interface is a **read-evaluate-print loop** (REPL). It is called
so because when you type a command and press <kbd>Return</kbd> (also known as <kbd>Enter</kbd>) the shell
reads your command,
evaluates (or "executes") it,
prints the output of your command,
loops back and waits for you to enter another command.
 
## The Shell


The Shell is a program which runs other programs rather than doing calculations itself.
The most popular Unix shell is Bash, (the Bourne Again SHell --- so-called because 
it's derived from a shell written by Stephen Bourne).
Bash is the default shell on most modern implementations of Unix
and in most packages that provide Unix-like tools for Windows.

## What does it look like?

A typical shell window looks something like:

~~~bash
dri9634@DSSLOAN MINGW64 ~$ 
dri9634@DSSLOAN MINGW64 ~$ ls -F
'3D Objects'/
 AppData/
'Application Data'@
 Contacts/
 Cookies@
 Desktop/
 Documents/
 Downloads/
 Favorites/
 IntelGraphicsProfiles/
 Links/
'Local Settings'@
 MicrosoftEdgeBackups/
 Music/
'My Documents'@
 NetHood@
 NTUSER.DAT
 ntuser.dat.LOG1
 ntuser.dat.LOG2
 NTUSER.DAT{8ebe95f7-3dcb-11e8-a9d9-7cfe90913f50}.TM.blf
 NTUSER.DAT{8ebe95f7-3dcb-11e8-a9d9-7cfe90913f50}.TMContainer00000000000000000001.regtrans-ms
 NTUSER.DAT{8ebe95f7-3dcb-11e8-a9d9-7cfe90913f50}.TMContainer00000000000000000002.regtrans-ms
 ntuser.ini
 ntuser.pol
 OneDrive/
 Pictures/
 PrintHood@
 Recent@
'Saved Games'/
 Searches/
 SendTo@
'Start Menu'@
 Templates@
 Videos/
dri9634@DSSLOAN MINGW64 ~$
~~~

The first line shows only a **prompt**,
indicating that the shell is waiting for input.
Your shell may use different text for the prompt. Most importantly: 
when typing commands, either from these lessons or from other sources,
*do not type the prompt*, only the commands that follow it.

The part that you type,
`ls -F /` in the second line of the example,
typically has the following structure: a **command**,
some **flags** (also called **options** or **switches**) and an **argument**.
Flags start with a single dash (`-`) or two dashes (`--`), and change the behaviour of a command.
Arguments tell the command what to operate on (e.g. files and directories).
Sometimes flags and arguments are referred to as parameters.
A command can be called with more than one flag and more than one argument: but a
command doesn't always require an argument or a flag.

In the second line of the example above, our **command** is `ls`, with a **flag** `-F` and an
**argument** `/`. Each part is separated by spaces: if you omit the space 
between `ls` and `-F` the shell will look for a command called `ls-F`, which 
doesn't exist. Also, capitalization matters: `LS` is different from `ls`. 

Next we see the output that our command produced. In this case it is a listing 
of files and folders in a location called `/` - we'll cover what all these mean 
later today. Those using Windows might recognize the output in this example.

Finally, the shell again prints the prompt and waits for you to type the next 
command.

In the examples for this lesson, we'll show the prompt as `$ `. You can make your 
prompt look the same by executing the command `PS1='$ '`. But you can also leave 
your prompt as it is - often the prompt includes useful information about who and where 
you are.

Open a shell window and try executing `ls -F /` for yourself (don't forget that spaces
and capitalization are important!). You can change the prompt too, if you like.

## How does the shell know what `ls` and its flags mean?

Every command is a program stored somewhere on the computer, and the shell keeps a
list of places to search for commands (the list is in a **variable** called `PATH`, 
but those are concepts we'll meet later and are not too important at the moment). Recall
that commands, flags and arguments are separated by spaces.

So let's look at the REPL (read-evaluate-print loop) in more detail. Notice that the
"evaluate" step is made of two parts:

1. Read what was typed (`ls -F /` in our example)  
    The shell uses the spaces to split the line into the command, flags, and arguments
2. Evaluate:  
    a. Find a program called `ls`  
    b. Execute it, passing it the flags and arguments (`-F` and `/`) to 
       interpret as the program sees fit 
3. Print the output produced by the program

and then print the prompt and wait for you to enter another command.

> ## Command not found 
> If the shell can't find a program whose name is the command you typed, it 
> will print an error message like:
> 
> ~~~bash
> $ ls-F
> ~~~
> ~~~output
> -bash: ls-F: command not found
> ~~~
> 
> Usually this means that you have mis-typed the command - in this case we omitted
> the space between `ls` and `-F`. 


## Is it difficult?

It is a different model of interacting than a GUI, and that 
will take some effort - and some time - to learn. A GUI 
presents you with choices and you select one. With a **command line interface** (CLI) the choices are combinations 
of commands and parameters, more like words in a language than buttons on a screen. They
are not presented to you so
you must learn a few, like learning some vocabulary in a new language. But a small 
number of commands gets you a long way, and we'll cover those essential few today.

## Flexibility and automation 

The grammar of a shell allows you to combine existing tools into powerful
pipelines and handle large volumes of data automatically. Sequences of
commands can be written into a *script*, improving the reproducibility of 
workflows and allowing you to repeat them easily.

In addition, the command line is often the easiest way to interact with remote machines and supercomputers.
Familiarity with the shell is near essential to run a variety of specialized tools and resources
including high-performance computing systems.
As clusters and cloud computing systems become more popular for scientific data crunching,
being able to interact with the shell is becoming a necessary skill.
We can build on the command-line skills covered here
to tackle a wide range of scientific questions and computational challenges.

## Software Carpentry's story - Nelle's Pipeline: Starting Point

Nelle Nemo, a marine biologist,
has just returned from a six-month survey of the
[North Pacific Gyre](http://en.wikipedia.org/wiki/North_Pacific_Gyre),
where she has been sampling gelatinous marine life in the
[Great Pacific Garbage Patch](http://en.wikipedia.org/wiki/Great_Pacific_Garbage_Patch).
She has 1520 samples in all and now needs to:

1.  Run each sample through an assay machine
    that will measure the relative abundance of 300 different proteins.
    The machine's output for a single sample is
    a file with one line for each protein.
2.  Calculate statistics for each of the proteins separately
    using a program her supervisor wrote called `goostats`.
3.  Write up results.
    Her supervisor would really like her to do this by the end of the month
    so that her paper can appear in an upcoming special issue of *Aquatic Goo Letters*.

It takes about half an hour for the assay machine to process each sample.
The good news is that
it only takes two minutes to set each one up.
Since her lab has eight assay machines that she can use in parallel,
this step will "only" take about two weeks.

The bad news is that if she has to run `goostats` by hand using a GUI,
she'll have to select a file using an open file dialog 1520 times.
At 30 seconds per sample,
the whole process will take more than 12 hours
(and that's assuming the best-case scenario where she is ready to select the next file
as soon as the previous sample analysis has finished).
This zero-breaks always-ready scenario is only achievable by a machine so it would
likely take much longer than 12 hours, not to mention that
the chances of her selecting all of those files correctly are practically zero.
Missing that paper deadline is looking increasingly likely.

The next few lessons will explore what she should do instead.
More specifically,
they explain how she can use a command shell to run the `goostats` program,
using loops to automate the repetitive steps e.g. entering file names,
so that her computer can work 24 hours a day while she writes her paper.

As a bonus,
once she has put a processing pipeline together,
she will be able to use it again whenever she collects more data.

## Key Points
* A shell is a program whose primary purpose is to read commands and run other programs.
* The shell’s main advantages are its high action-to-keystroke ratio, its support for automating repetitive tasks, and its capacity to access networked machines.
* The shell’s main disadvantages are its primarily textual nature and how cryptic its commands and operation can be.
