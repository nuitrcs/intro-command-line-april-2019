# Practice 3 

These are during-workshop exercises that correspond to the third command line script

## Creating Files a Different Way

We have seen how to create text files using the `vi` editor.
Now, try the following command:

~~~bash
$ touch my_file.txt
~~~


1.  What did the `touch` command do?
    When you look at your current directory using the GUI file explorer,
    does the file show up?

2.  Use `ls -l` to inspect the files.  How large is `my_file.txt`?

3.  When might you want to create a file this way?


## Moving to the Current Folder

After running the following commands,
Jamie realizes that she put the files `sucrose.dat` and `maltose.dat` into the wrong folder:

~~~bash
$ ls -F
  analyzed/ raw/
$ ls -F analyzed
  fructose.dat glucose.dat maltose.dat sucrose.dat
$ cd raw/
~~~

Fill in the blanks to move these files to the current folder
(i.e., the one she is currently in):

~~~bash
$ mv ___/sucrose.dat  ___/maltose.dat ___
~~~

## Renaming Files

Suppose that you created a plain-text file in your current directory to contain a list of the
statistical tests you will need to do to analyze your data, and named it: `statstics.txt`

After creating and saving this file you realize you misspelled the filename! You want to
correct the mistake, which of the following commands could you use to do so?

1. `cp statstics.txt statistics.txt`
2. `mv statstics.txt statistics.txt`
3. `mv statstics.txt .`
4. `cp statstics.txt .`

## Moving and Copying

What is the output of the closing `ls` command in the sequence shown below?

~~~bash
$ pwd
~~~
~~~output
/Users/jamie/data
~~~
~~~bash
$ ls
~~~
~~~output
proteins.dat
~~~
~~~bash
$ mkdir recombine
$ mv proteins.dat recombine/
$ cp recombine/proteins.dat ../proteins-saved.dat
$ ls
~~~

1.   `proteins-saved.dat recombine`
2.   `recombine`
3.   `proteins.dat recombine`
4.   `proteins-saved.dat`


## Using rm Safely

What happens when we execute `rm -i thesis_backup/quotations.txt`?
Why would we want this protection when using `rm`?

## Copy with Multiple Filenames

For this exercise, you can test the commands in the `data-shell/data` directory.

In the example below, what does `cp` do when given several filenames and a directory name?

~~~bash
$ mkdir backup
$ cp amino-acids.txt animals.txt backup/
~~~

In the example below, what does `cp` do when given three or more file names?

~~~bash
$ ls -F
~~~
~~~output
amino-acids.txt  animals.txt  backup/  elements/  morse.txt  pdb/  planets.txt  salmon.txt  sunspot.txt
~~~
~~~bash
$ cp amino-acids.txt animals.txt morse.txt 
~~~

## List filenames matching a pattern

When run in the `molecules` directory, which `ls` command(s) will
produce this output?

`ethane.pdb   methane.pdb`

1. `ls *t*ane.pdb`
2. `ls *t?ne.*`
3. `ls *t??ne.pdb`
4. `ls ethane.*`

## More on Wildcards

Sam has a directory containing calibration data, datasets, and descriptions of
the datasets:

~~~
2015-10-23-calibration.txt
2015-10-23-dataset1.txt
2015-10-23-dataset2.txt
2015-10-23-dataset_overview.txt
2015-10-26-calibration.txt
2015-10-26-dataset1.txt
2015-10-26-dataset2.txt
2015-10-26-dataset_overview.txt
2015-11-23-calibration.txt
2015-11-23-dataset1.txt
2015-11-23-dataset2.txt
2015-11-23-dataset_overview.txt
~~~

Before heading off to another field trip, she wants to back up her data and
send some datasets to her colleague Bob. Sam uses the following commands
to get the job done:

~~~
$ cp *dataset* /backup/datasets
$ cp ____calibration____ /backup/calibration
$ cp 2015-____-____ ~/send_to_bob/all_november_files/
$ cp ____ ~/send_to_bob/all_datasets_created_on_a_23rd/
~~~

Help Sam by filling in the blanks.


## Organizing Directories and Files

Jamie is working on a project and she sees that her files aren't very well
organized:

~~~bash
$ ls -F
~~~
~~~output
analyzed/  fructose.dat    raw/   sucrose.dat
~~~

The `fructose.dat` and `sucrose.dat` files contain output from her data
analysis. What command(s) covered in this lesson does she need to run so that the commands below will
produce the output shown?

~~~bash
$ ls -F
~~~
~~~output
analyzed/   raw/
~~~
~~~bash
$ ls analyzed
~~~
~~~output
fructose.dat    sucrose.dat
~~~

## Reproduce a folder structure

You're starting a new experiment, and would like to duplicate the directory
structure from your previous experiment so you can add new data.

Assume that the previous experiment is in a folder called '2016-05-18',
which contains a `data` folder that in turn contains folders named `raw` and
`processed` that contain data files.  The goal is to copy the folder structure
of the `2016-05-18-data` folder into a folder called `2016-05-20`
so that your final directory structure looks like this:

2016-05-20/
└── data
    ├── processed
    └── raw
 
Which of the following set of commands would achieve this objective?
What would the other commands do?

~~~bash
$ mkdir 2016-05-20
$ mkdir 2016-05-20/data
$ mkdir 2016-05-20/data/processed
$ mkdir 2016-05-20/data/raw
~~~
~~~bash
$ mkdir 2016-05-20
$ cd 2016-05-20
$ mkdir data
$ cd data
$ mkdir raw processed
~~~
~~~bash
$ mkdir 2016-05-20/data/raw
$ mkdir 2016-05-20/data/processed
~~~
~~~bash
$ mkdir 2016-05-20
$ cd 2016-05-20
$ mkdir data
$ mkdir raw processed
~~~
