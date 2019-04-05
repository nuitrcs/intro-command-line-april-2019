# Command Line Session 2 - "Working With Files and Directories"

---
This is the material we'll cover during the third part of the workshop.  We may deviate a little, but we'll work from this.

We'll continue working exclusively in Command line.  

Questions for this session:
- "How can I create, copy, and delete files and directories?"
- "How can I edit files?"

Objectives for this session:
- "Create a directory hierarchy that matches a given diagram."
- "Create files in that hierarchy using an editor or by copying and renaming existing files."
- "Delete, copy and move specified files and/or directories."
---

## Creating directories
We now know how to explore files and directories,
but how do we create them in the first place?

### Step one: see where we are and what we already have
Let's go back to our `data-shell` directory on the Desktop
and use `ls -F` to see what it contains:

~~~bash
$ pwd
~~~

~~~output
/c/Users/dri9634/Desktop/data-shell
~~~


~~~bash
$ ls -F
~~~

~~~output
creatures/  data/  molecules/  north-pacific-gyre/  notes.txt  pizza.cfg  solar.pdf  writing/
~~~


### Create a directory

Let's create a new directory called `thesis` using the command `mkdir thesis`
(which has no output):

~~~bash
$ mkdir thesis
~~~

As you might guess from its name,
`mkdir` means "make directory".
Since `thesis` is a relative path
(i.e., does not have a leading slash, like `/what/ever/thesis`),
the new directory is created in the current working directory:

~~~bash
$ ls -F
~~~

~~~output
creatures/  data/  molecules/  north-pacific-gyre/  notes.txt  pizza.cfg  solar.pdf  thesis/  writing/
~~~

> ## Two ways of doing the same thing
> Using the shell to create a directory is no different than using a file explorer.
> If you open the current directory using your operating system's graphical file explorer,
> the `thesis` directory will appear there too.
> While the shell and the file explorer are two different ways of interacting with the files,
> the files and directories themselves are the same.

> ## Good names for files and directories
>
> Complicated names of files and directories can make your life painful
> when working on the command line. Here we provide a few useful
> tips for the names of your files.
>
> 1. Don't use spaces.
>
>    Spaces can make a name more meaningful,
>    but since spaces are used to separate arguments on the command line
>    it is better to avoid them in names of files and directories.
>    You can use `-` or `_` instead (e.g. `north-pacific-gyre/` rather than `north pacific gyre/`).
>
> 2. Don't begin the name with `-` (dash).
>
>    Commands treat names starting with `-` as options.
>
> 3. Stick with letters, numbers, `.` (period or 'full stop'), `-` (dash) and `_` (underscore).
>
>    Many other characters have special meanings on the command line.
>    We will learn about some of these during this lesson.
>    There are special characters that can cause your command to not work as
>    expected and can even result in data loss.
>
> If you need to refer to names of files or directories that have spaces
> or other special characters, you should surround the name in quotes (`""`).

Since we've just created the `thesis` directory, there's nothing in it yet:

~~~bash
$ ls -F thesis
~~~

### Create a text file
Let's change our working directory to `thesis` using `cd`,
then run a text editor called Nano to create a file called `draft.txt`:

~~~
$ cd thesis
$ vi draft.txt
~~~

> ## Which Editor?
>
> When we say, "`vi` is a text editor," we really do mean "text": it can
> only work with plain character data, not tables, images, or any other
> human-friendly media. We use it in examples because it is a default editor 
> on most systems. On Unix systems (such as Linux and Mac OS X),
> many programmers use [Emacs](http://www.gnu.org/software/emacs/) or
> [Vim](http://www.vim.org/), 
> or a graphical editor such as
> [Gedit](http://projects.gnome.org/gedit/). On Windows, you may wish to
> use [Notepad++](http://notepad-plus-plus.org/).  Windows also has a built-in
> editor called `notepad` that can be run from the command line in the same
> way as `vi` for the purposes of this lesson.  
>
> No matter what editor you use, you will need to know where it searches
> for and saves files. If you start it from the shell, it will (probably)
> use your current working directory as its default location. If you use
> your computer's start menu, it may want to save files in your desktop or
> documents directory instead. You can change this by navigating to
> another directory the first time you "Save As..."

Let's type in a few lines of text. To start typing we need to press <kbd>i</kbd> to **I**nsert text.
Once we're happy with our text, we can press <kbd>Ctrl</kbd>+<kbd>c</kbd> (press the Ctrl or Control key and, while
holding it down, press the c key) and then <kbd>:</kbd><kbd>x</kbd> to write our data to disk
(we'll not be asked vi will save this to the suggested file `draft.txt` and will return to the command prompt).

> More information about `vi` is found in the resource section.

`vi` doesn't leave any output on the screen after it exits,
but `ls` now shows that we have created a file called `draft.txt`:

~~~bash
$ ls
~~~

~~~output
draft.txt
~~~

[Exercise](commandline-exercise3.md#Creating-Files-a-Different-Way)

## What's In A Name

You may have noticed that all of Nelle's files are named "something dot
something", and in this part of the lesson, we always used the extension
`.txt`.  This is just a convention: we can call a file `mythesis` or
almost anything else we want. However, most people use two-part names
most of the time to help them (and their programs) tell different kinds
of files apart. The second part of such a name is called the
**filename extension**, and indicates
what type of data the file holds: `.txt` signals a plain text file, `.pdf`
indicates a PDF document, `.cfg` is a configuration file full of parameters
for some program or other, `.png` is a PNG image, and so on.

This is just a convention, albeit an important one. Files contain
bytes: it's up to us and our programs to interpret those bytes
according to the rules for plain text files, PDF documents, configuration
files, images, and so on.

Naming a PNG image of a whale as `whale.mp3` doesn't somehow
magically turn it into a recording of whalesong, though it *might*
cause the operating system to try to open it with a music player
when someone double-clicks it.

## Moving files and directories
Returning to the `data-shell` directory,

```bash
cd ~/Desktop/data-shell/
```

In our `thesis` directory we have a file `draft.txt`
which isn't a particularly informative name,
so let's change the file's name using `mv`,
which is short for "move":

~~~
$ mv thesis/draft.txt thesis/quotes.txt
~~~

The first argument tells `mv` what we're "moving",
while the second is where it's to go.
In this case,
we're moving `thesis/draft.txt` to `thesis/quotes.txt`,
which has the same effect as renaming the file.
Sure enough,
`ls` shows us that `thesis` now contains one file called `quotes.txt`:

~~~bash
$ ls thesis
~~~

~~~
quotes.txt
~~~

One has to be careful when specifying the target file name, since `mv` will
silently overwrite any existing file with the same name, which could
lead to data loss. An additional flag, `mv -i` (or `mv --interactive`),
can be used to make `mv` ask you for confirmation before overwriting.

Note that `mv` also works on directories.

Let's move `quotes.txt` into the current working directory.
We use `mv` once again,
but this time we'll just use the name of a directory as the second argument
to tell `mv` that we want to keep the filename,
but put the file somewhere new.
(This is why the command is called "move".)
In this case,
the directory name we use is the special directory name `.` that we mentioned earlier.

~~~bash
$ mv thesis/quotes.txt .
~~~

The effect is to move the file from the directory it was in to the current working directory.
`ls` now shows us that `thesis` is empty:

~~~bash
$ ls thesis
~~~

Further,
`ls` with a filename or directory name as an argument only lists that file or directory.
We can use this to see that `quotes.txt` is still in our current directory:

~~~bash
$ ls quotes.txt
~~~

~~~output
quotes.txt
~~~

[Exercise](commandline-exercise3.md#Moving-to-the-Current-Folder)

## Copying files and directories

The `cp` command works very much like `mv`,
except it copies a file instead of moving it.
We can check that it did the right thing using `ls`
with two paths as arguments --- like most Unix commands,
`ls` can be given multiple paths at once:

~~~bash
$ cp quotes.txt thesis/quotations.txt
$ ls quotes.txt thesis/quotations.txt
~~~

~~~output
quotes.txt   thesis/quotations.txt
~~~

We can also copy a directory and all its contents by using the
[recursive](https://en.wikipedia.org/wiki/Recursion) flag `-r`,
e.g. to back up a directory:

```bash
$ cp -r thesis thesis_backup
```

We can check the result by listing the contents of both the `thesis` and `thesis_backup` directory:

```bash
$ ls thesis thesis_backup
```

```output
thesis:
quotations.txt

thesis_backup:
quotations.txt
```
[Exercise](commandline-exercise3.md#Renaming-Files)

[Exercise](commandline-exercise3.md#Moving-and-Copying)


## Removing files and directories

Returning to the `data-shell` directory,
let's tidy up this directory by removing the `quotes.txt` file we created.
The Unix command we'll use for this is `rm` (short for 'remove'):

~~~bash
$ rm quotes.txt
~~~

We can confirm the file has gone using `ls`:

~~~bash
$ ls quotes.txt
~~~

```output
ls: cannot access 'quotes.txt': No such file or directory
```

> ## Deleting Is Forever
>
> The Unix shell doesn't have a trash bin that we can recover deleted
> files from (though most graphical interfaces to Unix do).  Instead,
> when we delete files, they are unlinked from the file system so that
> their storage space on disk can be recycled. Important word here is **unlinked**. Tools for finding and
> recovering deleted files do exist, but there's no guarantee they'll
> work in any particular situation, since the computer may recycle the
> file's disk space right away. Moral of the story if you have deleted something on Unix
> and you want it recovered stop doing whatever you were doing ask for help immediately
> and hope that computer was not doing something in the background.
> Probability that it did goes up with the importance of the deleted content.

[Exercise](commandline-exercise3.md#Using-rm-Safely)

If we try to remove the `thesis` directory using `rm thesis`,
we get an error message:

~~~bash
$ rm thesis
~~~

~~~output
rm: cannot remove `thesis': Is a directory
~~~

This happens because `rm` by default only works on files, not directories.

`rm` can remove a directory *and all its contents* if we use the 
recursive flag `-r`, and it will do so *without any confirmation prompts*:

~~~bash
$ rm -r thesis
~~~

Given that there is no way to retrieve files deleted using the shell,
`rm -r` *should be used with great caution* (you might consider adding the interactive flag `rm -r -i`).

## Operations with multiple files and directories

Oftentimes one needs to copy or move several files at once. This can be done by providing a list of individual filenames, or specifying a naming pattern using wildcards.  

[Exercise](commandline-exercise3.md#Copy-with-Multiple-Filenames)


### Using wildcards for accessing multiple files at once

> ## Wildcards
>
> `*` is a **wildcard**, which matches zero or more  characters.
> Let's consider the `data-shell/molecules` directory:
> `*.pdb` matches `ethane.pdb`, `propane.pdb`, and every
> file that ends with '.pdb'. On the other hand, `p*.pdb` only matches
> `pentane.pdb` and `propane.pdb`, because the 'p' at the front only
> matches filenames that begin with the letter 'p'.
>
> `?` is also a wildcard, but it matches exactly one character.
> So `?ethane.pdb` would match `methane.pdb` whereas
> `*ethane.pdb` matches both `ethane.pdb`, and `methane.pdb`.
>
> Wildcards can be used in combination with each other
> e.g. `???ane.pdb` matches three characters followed by `ane.pdb`,
> giving `cubane.pdb  ethane.pdb  octane.pdb`.
>
> When the shell sees a wildcard, it expands the wildcard to create a
> list of matching filenames *before* running the command that was
> asked for. As an exception, if a wildcard expression does not match
> any file, Bash will pass the expression as an argument to the command
> as it is. For example typing `ls *.pdf` in the `molecules` directory
> (which contains only files with names ending with `.pdb`) results in
> an error message that there is no file called `*.pdf`.
> However, generally commands like `wc` and `ls` see the lists of
> file names matching these expressions, but not the wildcards
> themselves. It is the shell, not the other programs, that deals with
> expanding wildcards, and this is another example of orthogonal design.

[Exercise](commandline-exercise3.md#List-filenames-matching-a-pattern)

## List filenames matching a pattern

When run in the `molecules` directory, which `ls` command(s) will
produce this output?

`ethane.pdb   methane.pdb`

1. `ls *t*ane.pdb`
2. `ls *t?ne.*`
3. `ls *t??ne.pdb`
4. `ls ethane.*`

[Exercise](commandline-exercise3.md#More-on-Wildcards)

[Exercise](commandline-exercise3.md#Organizing-Directories-and-Files)

[Exercise](commandline-exercise3.md#Reproduce-a-folder-structure)

## Key points

* `cp old new` copies a file.
* `mkdir path` creates a new directory.
* `mv old new` moves (renames) a file or directory.
* `rm path` removes (deletes) a file.
* `*` matches zero or more characters in a filename, so `*.txt` matches all files ending in `.txt`.
* `?` matches any single character in a filename, so `?.txt` matches `a.txt` but not `any.txt`.
* Use of the `Control` key may be described in many ways, including `Ctrl-C`, `Control-C`, and `^C`.
* The shell does not have a trash bin: once something is deleted, it’s really gone.
* Most files’ names are `something.extension`. The extension isn’t required, and doesn’t guarantee anything, but is normally used to indicate the type of data in the file.
* Depending on the type of work you do, you may need to choose the right editor for your work.
