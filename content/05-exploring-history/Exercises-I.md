+++
title = "f. Exercises I"
weight = 2
chapter = false
+++


## Recovering Older Versions of a File

 Jennifer has made changes to the Python script that she has been working on for weeks, and the
 modifications she made this morning "broke" the script and it no longer runs. She has spent
 ~ 1hr trying to fix it, with no luck...

 Luckily, she has been keeping track of her project's versions using Git! Which commands below will
 let her recover the last committed version of her Python script called
 `data_cruncher.py`?

 1. `$ git checkout HEAD`

 2. `$ git checkout HEAD data_cruncher.py`

 3. `$ git checkout HEAD~1 data_cruncher.py`

 4. `$ git checkout <unique ID of last commit data_cruncher.py`

 5. Both 2 and 4

{{% expand "Solution" %}}
 
  The answer is (5)-Both 2 and 4. 
  
  The `checkout` command restores files from the repository, overwriting the files in your working 
  directory. Answers 2 and 4 both restore the *latest* version *in the repository* of the file 
  `data_cruncher.py`. Answer 2 uses `HEAD` to indicate the *latest*, whereas answer 4 uses the 
  unique ID of the last commit, which is what `HEAD` means. 
  
  Answer 3 gets the version of `data_cruncher.py` from the commit *before* `HEAD`, which is NOT 
  what we wanted.
  
  Answer 1 can be dangerous! Without a filename, `git checkout` will restore **all files** 
  in the current directory (and all directories below it) to their state at the commit specified. 
  This command will restore `data_cruncher.py` to the latest commit version, but it will also 
  restore *any other files that are changed* to that version, erasing any changes you may 
  have made to those files!
  As discussed above, you are left in a *detached* `HEAD` state, and you don't want to be there.
  {{% /expand %}}

## Reverting a Commit

 Jennifer is collaborating with colleagues on her Python script.  She
 realizes her last commit to the project's repository contained an error, and 
 wants to undo it.  Jennifer wants to undo correctly so everyone in the project's
 repository gets the correct change. The command `git revert [erroneous commit ID]` will create a 
 new commit that reverses the erroneous commit.  
    
 The command `git revert` is
 different from `git checkout [commit ID]` because `git checkout` returns the
 files not yet committed within the local repository to a previous state, whereas `git revert`
 reverses changes committed to the local and project repositories.   
   
 Below are the right steps and explanations for Jennifer to use `git revert`,
 what is the missing command?  
 1. `________ # Look at the git history of the project to find the commit ID`

 2. Copy the ID (the first few characters of the ID, e.g. 0b1d055).

 3. `git revert [commit ID]`

 4. Type in the new commit message.

 5. Save and close
 
 
{{% expand "Solution" %}}
  The command `git log` lists project history with commit IDs.  
  
  The command `git show HEAD` shows changes made at the latest commit, and lists
  the commit ID; however, Jennifer should double-check it is the correct commit, and no one
  else has committed changes to the repository.
{{% /expand %}}

## Understanding Workflow and History

 What is the output of the last command in

 ```Bash
 $ cd planets
 $ echo "Venus is beautiful and full of love"  venus.txt
 $ git add venus.txt
 $ echo "Venus is too hot to be suitable as a base"  venus.txt
 $ git commit -m "Comment on Venus as an unsuitable base"
 $ git checkout HEAD venus.txt
 $ cat venus.txt #this will print the contents of venus.txt to the screen
 ```
 

 1. ```
    Venus is too hot to be suitable as a base
    ```
    
 2. ```
    Venus is beautiful and full of love
    ```
    
 3. ```
    Venus is beautiful and full of love
    Venus is too hot to be suitable as a base
    ```
    
 4. ```
    Error because you have changed venus.txt without committing the changes
    ```
    

{{% expand "Solution" %}} 
  The answer is 2. 
  
  The command `git add venus.txt` places the current version of `venus.txt` into the staging area. 
  The changes to the file from the second `echo` command are only applied to the working copy, 
  not the version in the staging area.
  
  So, when `git commit -m "Comment on Venus as an unsuitable base"` is executed, 
  the version of `venus.txt` committed to the repository is the one from the staging area and
  has only one line.
   
   At this time, the working copy still has the second line (and 
   `git status` will show that the file is modified). However, `git checkout HEAD venus.txt` 
   replaces the working copy with the most recently committed version of `venus.txt`.
   
   So, `cat venus.txt` will output 
   ```
   Venus is beautiful and full of love.
  ```
{{% /expand %}}
