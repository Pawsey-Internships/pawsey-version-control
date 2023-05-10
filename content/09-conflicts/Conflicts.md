+++
title = "a. Conflicts"
weight = 2
chapter = false
+++

As soon as people can work in parallel, they'll likely step on each other's
toes.  This will even happen with a single person: if we are working on
a piece of software on both our laptop and a server in the lab, we could make
different changes to each copy.  Version control helps us manage these
**conflicts** by giving us tools to
**resolve** overlapping changes.

To see how we can resolve conflicts, we must first create one.  The file
`mars.txt` currently looks like this in both partners' copies of our `planets`
repository:

```Bash
$ cat mars.txt
```


```
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
```


Let's add a line to the collaborator's copy only:

```Bash
$ nano mars.txt
$ cat mars.txt
```


```
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line added to Wolfman's copy
```


and then push the change to GitHub:

```Bash
$ git add mars.txt
$ git commit -m "Add a line in our home copy"
```


```
[main 5ae9631] Add a line in our home copy
 1 file changed, 1 insertion(+)
```


```Bash
$ git push origin main
```


```
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 331 bytes | 331.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/vlad/planets.git
   29aba7c..dabb4c8  main - main
```


Now let's have the owner
make a different change to their copy
*without* updating from GitHub:

```Bash
$ nano mars.txt
$ cat mars.txt
```


```
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
We added a different line in the other copy
```


We can commit the change locally:

```Bash
$ git add mars.txt
$ git commit -m "Add a line in my copy"
```


```
[main 07ebc69] Add a line in my copy
 1 file changed, 1 insertion(+)
```


but Git won't let us push it to GitHub:

```Bash
$ git push origin main
```


```
To https://github.com/vlad/planets.git
 ! [rejected]        main - main (fetch first)
error: failed to push some refs to 'https://github.com/vlad/planets.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```


![The Conflicting Changes](images/conflict.svg)

Git rejects the push because it detects that the remote repository has new updates that have not been
incorporated into the local branch.
What we have to do is pull the changes from GitHub,
**merge** them into the copy we're currently working in, and then push that.
Let's start by pulling:

```Bash
$ git pull origin main
```


```
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 3 (delta 2), reused 3 (delta 2), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/vlad/planets
 * branch            main     - FETCH_HEAD
    29aba7c..dabb4c8  main     - origin/main
Auto-merging mars.txt
CONFLICT (content): Merge conflict in mars.txt
Automatic merge failed; fix conflicts and then commit the result.
```

