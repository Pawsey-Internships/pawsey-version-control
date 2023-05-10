+++
title = "b. Exercises"
weight = 2
chapter = false
+++

## Ignoring Nested Files

 Given a directory structure that looks like:

 ```
 results/data
 results/plots
 ```
 

 How would you ignore only `results/plots` and not `results/data`?

{{% expand "Solution" %}} 
  If you only want to ignore the contents of
  `results/plots`, you can change your `.gitignore` to ignore
  only the `/plots/` subfolder by adding the following line to
  your .gitignore:
 
  ```
  results/plots/
  ```
  
 
  This line will ensure only the contents of `results/plots` is ignored, and
  not the contents of `results/data`.
 
  As with most programming issues, there
  are a few alternative ways that one may ensure this ignore rule is followed.
  The "Ignoring Nested Files: Variation" exercise has a slightly
  different directory structure
  that presents an alternative solution.
  Further, the discussion page has more detail on ignore rules.
{{% /expand %}}

## Including Specific Files

 How would you ignore all `.dat` files in your root directory except for
 `final.dat`?
 Hint: Find out what `!` (the exclamation point operator) does

{{% expand "Solution" %}} 
  You would add the following two lines to your .gitignore:
 
  ```
  *.dat           # ignore all data files
  !final.dat      # except final.data
  ```
  
 
  The exclamation point operator will include a previously excluded entry.
 
  Note also that because you've previously committed `.dat` files in this
  lesson they will not be ignored with this new rule. Only future additions
  of `.dat` files added to the root directory will be ignored.
{{% /expand %}}

## Ignoring Nested Files: Variation

 Given a directory structure that looks similar to the earlier Nested Files
 exercise, but with a slightly different directory structure:

 ```
 results/data
 results/images
 results/plots
 results/analysis
 ```
 

 How would you ignore all of the contents in the results folder, but not `results/data`?

 Hint: think a bit about how you created an exception with the `!` operator
 before.

{{% expand "Solution" %}} 
  If you want to ignore the contents of
  `results/` but not those of `results/data/`, you can change your `.gitignore` to ignore
  the contents of results folder, but create an exception for the contents of the
  `results/data` subfolder. Your .gitignore would look like this:
 
  ```
  results/*               # ignore everything in results folder
  !results/data/          # do not ignore results/data/ contents
  ```
{{% /expand %}}
 

## Ignoring all data Files in a Directory

 Assuming you have an empty .gitignore file, and given a directory structure that looks like:

 ```
 results/data/position/gps/a.dat
 results/data/position/gps/b.dat
 results/data/position/gps/c.dat
 results/data/position/gps/info.txt
 results/plots
 ```
 

 What's the shortest `.gitignore` rule you could write to ignore all `.dat`
 files in `result/data/position/gps`? Do not ignore the `info.txt`.

{{% expand "Solution" %}} 

  Appending `results/data/position/gps/*.dat` will match every file in `results/data/position/gps`
  that ends with `.dat`.
  The file `results/data/position/gps/info.txt` will not be ignored.
{{% /expand %}}

## Ignoring all data Files in the repository

 Let us assume you have many `.dat` files in different subdirectories of your repository.
 For example, you might have:
 
 ```
 results/a.dat
 data/experiment_1/b.dat
 data/experiment_2/c.dat
 data/experiment_2/variation_1/d.dat
 ```
 
 
 How do you ignore all the `.dat` files, without explicitly listing the names of the corresponding folders?
 
{{% expand "Solution" %}} 
  In the `.gitignore` file, write:
  
  ```
  **/*.dat               
  ```
  
 
  This will ignore all the `.dat` files, regardless of their position in the directory tree. 
  You can still include some specific exception with the exclamation point operator.
{{% /expand %}}

## The Order of Rules

 Given a `.gitignore` file with the following contents:

 ```
 *.dat
 !*.dat
 ```
 

 What will be the result?

{{% expand "Solution" %}} 
  The `!` modifier will negate an entry from a previously defined ignore pattern.
  Because the `!*.dat` entry negates all of the previous `.dat` files in the `.gitignore`,
  none of them will be ignored, and all `.dat` files will be tracked.
{{% /expand %}} 

## Log Files

 You wrote a script that creates many intermediate log-files of the form `log_01`, `log_02`, `log_03`, etc.
 You want to keep them but you do not want to track them through `git`.

 1. Write **one** `.gitignore` entry that excludes files of the form `log_01`, `log_02`, etc.

 2. Test your "ignore pattern" by creating some dummy files of the form `log_01`, etc.

 3. You find that the file `log_01` is very important after all, add it to the tracked files without changing the `.gitignore` again.

 4. Discuss with your neighbor what other types of files could reside in your directory that you do not want to track and thus would exclude via `.gitignore`.

{{% expand "Solution" %}} 
  1. append either `log_*`  or  `log*`  as a new entry in your .gitignore
  3. track `log_01` using   `git add -f log_01`
{{% /expand %}}
  
{{% notice note %}}
 ## `.gitconfig`
 The command `git config` is used to set Git configuration values on a global or local project level which correspond to `.gitconfig` text files.
 Executing `git config` like we did in setup will modify a configuration text file.
 Here is an example global `.gitconfig` file which we created from `git config --global`:
 ```
 [user]
 	email = Vlad Dracula
 	name = vlad@tran.sylvan.ia
 [pull]
 	rebase = true
 [credential]
 	helper = manager-core
 	helper = /usr/bin/git-credential-manager-core
 	credentialStore = gpg
 [github]
 	user = vladDracula
 ```
 
 But like `.gitignore` they can be added at a project level for specific behavours such as in the example above where we are
 telling git to use the rebase merge strategy instead of fast forward merge.
{{% /notice %}}
