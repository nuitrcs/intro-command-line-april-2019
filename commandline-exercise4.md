# Practice 4

These are during-workshop exercises that correspond to the fourth command line script

## What Does sort -n Do?

If we run `sort` on a file containing the following lines:

~~~source
10
2
19
22
6
~~~

the output is:

~~~output
10
19
2
22
6
~~~

If we run `sort -n` on the same input, we get this instead:

~~~output
2
6
10
19
22
~~~

Explain why `-n` has this effect.

## What Does Double Redirect Mean

We have seen the use of `>`, but there is a similar operator `>>` which works slightly differently.
We'll learn about the differences between these two operators by printing some strings.
We can use the `echo` command to print strings e.g.

~~~bash
$ echo The echo command prints text
~~~
~~~output
The echo command prints text
~~~
Now test the commands below to reveal the difference between the two operators:

~~~bash
$ echo hello > testfile01.txt
~~~

and:

~~~bash
$ echo hello >> testfile02.txt
~~~

Hint: Try executing each command twice in a row and then examining the output files.


## Appending Data

We have already met the `head` command, which prints lines from the start of a file.
`tail` is similar, but prints lines from the end of a file instead.

Consider the file `data-shell/data/animals.txt`.
After these commands, select the answer that
corresponds to the file `animals-subset.txt`:

~~~bash
$ head -n 3 animals.txt > animals-subset.txt
$ tail -n 2 animals.txt >> animals-subset.txt
~~~

1. The first three lines of `animals.txt`
2. The last two lines of `animals.txt`
3. The first three lines and the last two lines of `animals.txt`
4. The second and third lines of `animals.txt`

## Piping Commands Together

In our current directory, we want to find the 3 files which have the least number of
lines. Which command listed below would work?

1. `wc -l * > sort -n > head -n 3`
2. `wc -l * | sort -n | head -n 1-3`
3. `wc -l * | head -n 3 | sort -n`
4. `wc -l * | sort -n | head -n 3`

## What Does < Mean

Change directory to `data-shell` (the top level of our downloaded example data).

What is the difference between:

~~~bash
$ wc -l notes.txt
~~~

and:

~~~bash
$ wc -l < notes.txt
~~~


## Why Does uniq Only Remove Adjacent Duplicates

The command `uniq` removes adjacent duplicated lines from its input.
For example, the file `data-shell/data/salmon.txt` contains:

~~~source
coho
coho
steelhead
coho
steelhead
steelhead
~~~

Running the command `uniq salmon.txt` from the `data-shell/data` directory produces:

~~~output
coho
steelhead
coho
steelhead
~~~

Why do you think `uniq` only removes *adjacent* duplicated lines?
(Hint: think about very large data sets.) What other command could
you combine with it in a pipe to remove all duplicated lines?

## Pipe Reading Comprehension

A file called `animals.txt` (in the `data-shell/data` folder) contains the following data:

~~~source
2012-11-05,deer
2012-11-05,rabbit
2012-11-05,raccoon
2012-11-06,rabbit
2012-11-06,deer
2012-11-06,fox
2012-11-07,rabbit
2012-11-07,bear
~~~

What text passes through each of the pipes and the final redirect in the pipeline below?

~~~bash
$ cat animals.txt | head -n 5 | tail -n 3 | sort -r > final.txt
~~~
Hint: build the pipeline up one command at a time to test your understanding


## Pipe Construction

For the file `animals.txt` from the previous exercise, the command:

~~~bash
$ cut -d , -f 2 animals.txt
~~~

uses the `-d` flag to separate each line by comma, and the `-f` flag
to print the second field in each line, to give the following output:

~~~output
deer
rabbit
raccoon
rabbit
deer
fox
rabbit
bear
~~~

What other command(s) could be added to this in a pipeline to find
out what animals the file contains (without any duplicates in their
names)?


## Which Pipe

The file `animals.txt` contains 8 lines of data formatted as follows:

~~~output
2012-11-05,deer
2012-11-05,rabbit
2012-11-05,raccoon
2012-11-06,rabbit
...
~~~

Assuming your current directory is `data-shell/data/`,
what command would you use to produce a table that shows
the total count of each type of animal in the file?

1.  `grep {deer, rabbit, raccoon, deer, fox, bear} animals.txt | wc -l`
2.  `sort animals.txt | uniq -c`
3.  `sort -t, -k2,2 animals.txt | uniq -c`
4.  `cut -d, -f 2 animals.txt | uniq -c`
5.  `cut -d, -f 2 animals.txt | sort | uniq -c`
6.  `cut -d, -f 2 animals.txt | sort | uniq -c | wc -l`

## Wildcard Expressions

Wildcard expressions can be very complex, but you can sometimes write
them in ways that only use simple syntax, at the expense of being a bit
more verbose.  
Consider the directory `data-shell/north-pacific-gyre/2012-07-03` :
the wildcard expression `*[AB].txt`
matches all files ending in `A.txt` or `B.txt`. Imagine you forgot about
this.

1.  Can you match the same set of files with basic wildcard expressions
    that do not use the `[]` syntax? *Hint*: You may need more than one
    expression.

2.  The expression that you found and the expression from the lesson match the
    same set of files in this example. What is the small difference between the
    outputs?

3.  Under what circumstances would your new expression produce an error message
    where the original one would not?

## Removing Unneeded Files

Suppose you want to delete your processed data files, and only keep
your raw files and processing script to save storage.
The raw files end in `.dat` and the processed files end in `.txt`.
Which of the following would remove all the processed data files,
and *only* the processed data files?

1. `rm ?.txt`
2. `rm *.txt`
3. `rm * .txt`
4. `rm *.*`
