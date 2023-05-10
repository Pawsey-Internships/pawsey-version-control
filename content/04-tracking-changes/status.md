+++
title = "a. Git Status"
weight = 2
chapter = false
+++

First let's make sure we're still in the right directory.
You should be in the `planets` directory.

```Bash
$ cd ~/planets
```


Let's create a file called `mars.txt` that contains some notes
about the Red Planet's suitability as a base.
We'll use `nano` to edit the file;
you can use whatever editor you like.
In particular, this does not have to be the `core.editor` you set globally earlier. But remember, the bash command to create or edit a new file will depend on the editor you choose (it might not be `nano`). For a refresher on text editors, check out ["Which Editor?"](https://swcarpentry.github.io/shell-novice/03-create/) in [The Unix Shell](https://swcarpentry.github.io/shell-novice/) lesson.

```Bash
$ nano mars.txt
```


Type the text below into the `mars.txt` file:

```
Cold and dry, but everything is my favorite color
```


Let's first verify that the file was properly created by running the list command (`ls`):


```Bash
$ ls
```


```
mars.txt
```



`mars.txt` contains a single line, which we can see by running:

```Bash
$ cat mars.txt
```


```
Cold and dry, but everything is my favorite color
```


If we check the status of our project again,
Git tells us that it's noticed the new file:

```Bash
$ git status
```


```
On branch main

No commits yet

Untracked files:
   (use "git add <file>..." to include in what will be committed)

	mars.txt

nothing added to commit but untracked files present (use "git add" to track)
```


The "untracked files" message means that there's a file in the directory
that Git isn't keeping track of.
We can tell Git to track a file using `git add`:

```Bash
$ git add mars.txt
```


and then check that the right thing happened:

```
$ git status
```


```
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   mars.txt

```


This indicates git knows it is supposed to keep track of the mars.txt file
