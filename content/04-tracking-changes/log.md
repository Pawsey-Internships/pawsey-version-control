+++
title = "c. git log"
weight = 2
chapter = false
+++

If we want to know what we've done recently,
we can ask Git to show us the project's history using `git log`:

```Bash
$ git log
```


```
commit f22b25e3233b4645dabd0d81e651fe074bd8e73b
Author: Vlad Dracula <vlad@tran.sylvan.ia
Date:   Thu Aug 22 09:51:46 2013 -0400

    Start notes on Mars as a base
```


`git log` lists all commits  made to a repository in reverse chronological order.
The listing for each commit includes
the commit's full identifier
(which starts with the same characters as
the short identifier printed by the `git commit` command earlier),
the commit's author,
when it was created,
and the log message Git was given when the commit was created.

{{% notice note %}}
 ## Where Are My Changes?

 If we run `ls` at this point, we will still see just one file called `mars.txt`.
 That's because Git saves information about files' history
 in the special `.git` directory mentioned earlier
 so that our filesystem doesn't become cluttered
 (and so that we can't accidentally edit or delete an old version).
{{% /notice %}}

Now suppose Dracula adds more information to the file.
(Again, we'll edit with `nano` and then `cat` the file to show its contents;
you may use a different editor, and don't need to `cat`.)

```Bash
$ nano mars.txt
$ cat mars.txt
```


```
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
```


When we run `git status` now,
it tells us that a file it already knows about has been modified:

```Bash
$ git status
```


```
On branch main
Changes not staged for commit:
  (use "git add <file..." to update what will be committed)
  (use "git checkout -- <file..." to discard changes in working directory)

	modified:   mars.txt

no changes added to commit (use "git add" and/or "git commit -a")
```


The last line is the key phrase:
"no changes added to commit".
We have changed this file,
but we haven't told Git we will want to save those changes
(which we do with `git add`)
nor have we saved them (which we do with `git commit`).
So let's do that now. It is good practice to always review
our changes before saving them. We do this using `git diff`.
This shows us the differences between the current state
of the file and the most recently saved version:

```Bash
$ git diff
```


```
diff --git a/mars.txt b/mars.txt
index df0654a..315bf3a 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1 +1,2 @@
 Cold and dry, but everything is my favorite color
+The two moons may be a problem for Wolfman
```


The output is cryptic because
it is actually a series of commands for tools like editors and `patch`
telling them how to reconstruct one file given the other.
If we break it down into pieces:

1.  The first line tells us that Git is producing output similar to the Unix `diff` command
    comparing the old and new versions of the file.
2.  The second line tells exactly which versions of the file
    Git is comparing;
    `df0654a` and `315bf3a` are unique computer-generated labels for those versions.
3.  The third and fourth lines once again show the name of the file being changed.
4.  The remaining lines are the most interesting, they show us the actual differences
    and the lines on which they occur.
    In particular,
    the `+` marker in the first column shows where we added a line.
