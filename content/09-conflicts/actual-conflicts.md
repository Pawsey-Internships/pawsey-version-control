+++
title = "b. Actual Conflicts"
weight = 2
chapter = false
+++

{{% notice note %}}
 ## What a conflict actually looks like

 The `git pull` command updates the local repository to include those
 changes already included in the remote repository.
 After the changes from remote branch have been fetched, Git detects that changes made to the local copy 
 overlap with those made to the remote repository, and therefore refuses to merge the two versions to
 stop us from trampling on our previous work. The conflict is marked in
 in the affected file:

 ```Bash
 $ cat mars.txt
 ```
 

 ```
 Cold and dry, but everything is my favorite color
 The two moons may be a problem for Wolfman
 But the Mummy will appreciate the lack of humidity
 <<<<<<< HEAD
 We added a different line in the other copy
 =======
 This line added to Wolfman's copy
  dabb4c8c450e8475aee9b14b4383acc99f42af1d
 ```
 Most editors will have special highlighting for git conflicts which mades identification more easy. 
{{% /notice %}}

Our change is preceded by `<<<<<<< HEAD`.
Git has then inserted `=======` as a separator between the conflicting changes
and marked the end of the content downloaded from GitHub with ``.
(The string of letters and digits after that marker
identifies the commit we've just downloaded.)

It is now up to us to edit this file to remove these markers
and reconcile the changes.
We can do anything we want: keep the change made in the local repository, keep
the change made in the remote repository, write something new to replace both,
or get rid of the change entirely.
Let's replace (CTRL + K to delete line in nano) both so that the file looks like this:

```Bash
$ cat mars.txt
```


```
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
We removed the conflict on this line
```


To finish merging,
we add `mars.txt` to the changes being made by the merge
and then commit:

```Bash
$ git add mars.txt
$ git status
```


```
On branch main
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:

	modified:   mars.txt

```


```Bash
$ git commit -m "Merge changes from GitHub"
```


```
[main 2abf2b1] Merge changes from GitHub
```


Now we can push our changes to GitHub:

```Bash
$ git push origin main
```


```
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 645 bytes | 645.00 KiB/s, done.
Total 6 (delta 4), reused 0 (delta 0)
remote: Resolving deltas: 100% (4/4), completed with 2 local objects.
To https://github.com/vlad/planets.git
   dabb4c8..2abf2b1  main - main
```


Git keeps track of what we've merged with what,
so we don't have to fix things by hand again
when the collaborator who made the first change pulls again:

```Bash
$ git pull origin main
```


```
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 6 (delta 4), reused 6 (delta 4), pack-reused 0
Unpacking objects: 100% (6/6), done.
From https://github.com/vlad/planets
 * branch            main     - FETCH_HEAD
    dabb4c8..2abf2b1  main     - origin/main
Updating dabb4c8..2abf2b1
Fast-forward
 mars.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```


We get the merged file:

```Bash
$ cat mars.txt
```


```
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
We removed the conflict on this line
```


We don't need to merge again because Git knows someone has already done that.

Git's ability to resolve conflicts is very useful, but conflict resolution
costs time and effort, and can introduce errors if conflicts are not resolved
correctly. If you find yourself resolving a lot of conflicts in a project,
consider these technical approaches to reducing them:

- Pull from upstream more frequently, especially before starting new work
- Use topic branches to segregate work, merging to main when complete
- Make smaller more atomic commits
- Where logically appropriate, break large files into smaller ones so that it is
  less likely that two authors will alter the same file simultaneously

Conflicts can also be minimized with project management strategies:

- Clarify who is responsible for what areas with your collaborators
- Discuss what order tasks should be carried out in with your collaborators so
  that tasks expected to change the same lines won't be worked on simultaneously
- If the conflicts are stylistic churn (e.g. tabs vs. spaces), establish a
  project convention that is governing and use code style tools (e.g.
  `htmltidy`, `perltidy`, `rubocop`, etc.) to enforce, if necessary
