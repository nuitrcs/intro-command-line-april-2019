# Practice 2

These are during-workshop exercises that correspond to the second command line script

## Exploring More ls Flags

You can also use two flags at the same time. What does the command `ls` do when used 
with the `-l` flag? What about if you use both the `-l` and the `-h` flag?

Some of its output is about properties that we do not cover in this lesson (such
as file permissions and ownership), but the rest should be useful
nevertheless.

## Listing Recursively and By Time

The command `ls -R` lists the contents of directories recursively, i.e., lists
their sub-directories, sub-sub-directories, and so on at each level. The command
`ls -t` lists things by time of last change, with most recently changed files or
directories first.
In what order does `ls -R -t` display things? Hint: `ls -l` uses a long listing
format to view timestamps.

## Absolute vs Relative Paths

Starting from `/c/Users/amanda/data/`,
which of the following commands could Amanda use to navigate to her home directory,
which is `/c/Users/amanda`?

1. `cd .`
2. `cd /`
3. `cd /c/Users/amanda`
4. `cd ../..`
5. `cd ~`
6. `cd home`
7. `cd ~/data/..`
8. `cd`
9. `cd ..`

## Relative Path Resolution

Using the filesystem diagram below, if `pwd` displays `/Users/thing`,
what will `ls -F ../backup` display?

1.  `../backup: No such file or directory`
2.  `2012-12-01 2013-01-08 2013-01-27`
3.  `2012-12-01/ 2013-01-08/ 2013-01-27/`
4.  `original/ pnas_final/ pnas_sub/`

![File System for Challenge Questions](http://swcarpentry.github.io/shell-novice/fig/filesystem-challenge.svg)

##  ls Reading Comprehension

Using the filesystem diagram below,
if `pwd` displays `/Users/backup`,
and `-r` tells `ls` to display things in reverse order,
what command(s) will result in the following output:

~~~output
pnas_sub/ pnas_final/ original/
~~~

![File System for Challenge Questions](http://swcarpentry.github.io/shell-novice/fig/filesystem-challenge.svg)

1.  `ls pwd`
2.  `ls -r -F`
3.  `ls -r -F /Users/backup`
