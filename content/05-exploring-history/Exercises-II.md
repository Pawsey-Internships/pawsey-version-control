+++
title = "g. Exercises II"
weight = 2
chapter = false
+++


## Checking Understanding of `git diff`

 Consider this command: `git diff HEAD~9 mars.txt`. What do you predict this command
 will do if you execute it? What happens when you do execute it? Why?

 Try another command, `git diff [ID] mars.txt`, where [ID] is replaced with
 the unique identifier for your most recent commit. What do you think will happen,
 and what does happen?

## Getting Rid of Staged Changes

 `git checkout` can be used to restore a previous commit when unstaged changes have
 been made, but will it also work for changes that have been staged but not committed?
 Make a change to `mars.txt`, add that change, and use `git checkout` to see if
 you can remove your change.

## Explore and Summarize Histories

 Exploring history is an important part of Git, and often it is a challenge to find
 the right commit ID, especially if the commit is from several months ago.

 Imagine the `planets` project has more than 50 files.
 You would like to find a commit that modifies some specific text in `mars.txt`.
 When you type `git log`, a very long list appeared.
 How can you narrow down the search?

 Recall that the `git diff` command allows us to explore one specific file,
 e.g., `git diff mars.txt`. We can apply a similar idea here.

 ```Bash
 $ git log mars.txt
 ```
 

 Unfortunately some of these commit messages are very ambiguous, e.g., `update files`.
 How can you search through these files?

 Both `git diff` and `git log` are very useful and they summarize a different part of the history 
 for you.
 Is it possible to combine both? Let's try the following:

 ```
 $ git log --patch mars.txt
 ```
 

 You should get a long list of output, and you should be able to see both commit messages and 
 the difference between each commit.

 Question: What does the following command do?

 ```
 $ git log --patch HEAD~9 *.txt
 ```
 

## How to change your last commit

 Sometimes you will find you might want to add things to your last commit. For example you might
 have broken a build or want to change formatting. Instead of creating a completely separate commit
 or rebasing you can simply run:
 ```
  $ git commit --ammend
 ```
 

  It will take your existing staged changes
 and add them to the current commit by creating a whole new commit will all the changes combined.
 When you commit you are given the opporutnity to reword your commit message or you can simply leave
 it unchanged.

 Make a change to mars.txt and ammend your last commit with a new message
{{% expand "Solution" %}}
 
  lets add some output
   ```
  $ echo "A small fix"  mars.txt
  ```
  
 
  Next we will ammend our last commit
   ```
  $ git commit --amend
  ```
  
  After changing the message running
   ```
  $ git log
  ```
  
   Should show that the most recent commit has the message you just wrote and running:
   ```
  $ git diff HEAD HEAD~1
  ```
  
  Should show that the most recent commit also includes "A small fix".
{{% /expand %}}
 You can use ammending to undo mistakes in a commit but depending on the scenario it might not
 be the most simple solution.



{{% notice note %}}
 ## Get help to undo almost anything

 [Seth Robertson's guide](https://sethrobertson.github.io/GitFixUm/fixup.html)
 is a one stop "choose your own adventure shop" for undoing things in git. If you get
 stuck follow this guide.
{{% /notice %}}
