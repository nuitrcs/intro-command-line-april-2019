# Practice Finding Things

These are during-workshop exercises that correspond to Finding Things material

## Using `grep`

Which command would result in the following output:

~~~
and the presence of absence:
~~~

1. `grep "of" haiku.txt`
2. `grep -E "of" haiku.txt`
3. `grep -w "of" haiku.txt`
4. `grep -i "of" haiku.txt`

## Wildcards

`grep`'s real power doesn't come from its options, though; it comes from the fact that patterns can include wildcards. (The technical name for
these is **regular expressions**, which is what the "re" in "grep" stands for.) Regular expressions are both complex
and powerful; if you want to do complex searches, please look at the lesson on [regexp software carpentry](http://v4.software-carpentry.org/regexp/index.html). As a taster, we can
find lines that have an 'o' in the second position like this:

~~~
$ grep -E '^.o' haiku.txt
~~~
~~~
You bring fresh toner.
Today it is not working
Software is like that.
~~~

We use the `-E` option and put the pattern in quotes to prevent the shell from trying to interpret it. (If the pattern contained a `*`, for
example, the shell would try to expand it before running `grep`.) The `^` in the pattern anchors the match to the start of the line. The `.`
matches a single character (just like `?` in the shell), while the `o` matches an actual 'o'.

## Tracking a Species

Leah has several hundred data files saved in one directory, each of which is formatted like this:

~~~
2013-11-05,deer,5
2013-11-05,rabbit,22
2013-11-05,raccoon,7
2013-11-06,rabbit,19
2013-11-06,deer,2
~~~

She wants to write a shell script that takes a species as the first command-line argument and a directory as the second argument. The script should return one file called `species.txt`
containing a list of dates and the number of that species seen on each date. For example using the data shown above, `rabbit.txt` would contain:

~~~
2013-11-05,22
2013-11-06,19
~~~

Put these commands and pipes in the right order to achieve this:
~~~
cut -d : -f 2
>
|
grep -w $1 -r $2
|
$1.txt
cut -d , -f 1,3
~~~

Hint: use `man grep` to look for how to grep text recursively in a directory and `man cut` to select more than one field in a line.

An example of such a file is provided in `data-shell/data/animal-counts/animals.txt`

## Little Women

You and your friend, having just finished reading *Little Women* by Louisa May Alcott, are in an argument.  Of the four sisters in the
book, Jo, Meg, Beth, and Amy, your friend thinks that Jo was the most mentioned.  You, however, are certain it was Amy.  Luckily, you
have a file `LittleWomen.txt` containing the full text of the novel (`data-shell/writing/data/LittleWomen.txt`).
Using a `for` loop, how would you tabulate the number of times each of the four sisters is mentioned?

Hint: one solution might employ the commands `grep` and `wc` and a `|`, while another might utilize `grep` options.
There is often more than one way to solve a programming task, so a particular solution is usually chosen based on a combination of
yielding the correct result, elegance, readability, and speed.


## Matching and Subtracting

The `-v` option to `grep` inverts pattern matching, so that only lines which do *not* match the pattern are printed. Given that, which of
the following commands will find all files in `/data` whose names end in `s.txt` (e.g., `animals.txt` or `planets.txt`), but do
*not* contain the word `net`? Once you have thought about your answer, you can test the commands in the `data-shell` directory.

1.  `find data -name '*s.txt' | grep -v net`
2.  `find data -name *s.txt | grep -v net`
3.  `grep -v "temp" $(find data -name '*s.txt')`
4.  None of the above.

## `find` Pipeline Reading Comprehension

Write a short explanatory comment for the following shell script:
~~~
wc -l $(find . -name '*.dat') | sort -n
~~~

## Finding Files With Different Properties

The `find` command can be given several other criteria known as "tests" to locate files with specific attributes, such as creation time, size,
permissions, or ownership.  Use `man find` to explore these, and then write a single command to find all files in or below the current directory
that are owned by the user `ahmed` and were modified in the last 24 hours.

Hint 1: you will need to use three tests: `-type`, `-mtime`, and `-user`.

Hint 2: The value for `-mtime` will need to be negative---why?

