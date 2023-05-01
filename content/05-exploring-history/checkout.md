+++
title = "b. Git checkout"
weight = 2
chapter = false
+++

We can put things back the way they were
by using `git checkout`:

```Bash
$ git checkout HEAD mars.txt
$ cat mars.txt
```


```Bash
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
```


As you might guess from its name,
`git checkout` checks out (i.e., restores) an old version of a file.
In this case,
we're telling Git that we want to recover the version of the file recorded in `HEAD`,
which is the last saved commit.
If we want to go back even further,
we can use a commit identifier instead:

```Bash
$ git checkout f22b25e mars.txt
```


```Bash
$ cat mars.txt
```


```
Cold and dry, but everything is my favorite color
```


```Bash
$ git status
```


```
On branch main
Changes to be committed:
  (use "git reset HEAD <file..." to unstage)

    modified:   mars.txt

```


Notice that the changes are currently in the staging area.
Again, we can put things back the way they were
by using `git checkout`:

```Bash
$ git checkout HEAD mars.txt
```
