+++
title = "d. Exercises "
weight = 2
chapter = false
+++

## GitHub GUI

 Browse to your `planets` repository on GitHub.
 Under the Code tab, find and click on the text that says "XX commits" (where "XX" is some number).
 Hover over, and click on, the three buttons to the right of each commit.
 What information can you gather/explore from these buttons?
 How would you get that same information in the shell?

{{% expand "Solution" %}}
## Solution
  The left-most button (with the picture of a clipboard) copies the full identifier of the commit 
  to the clipboard. In the shell, ```git log``` will show you the full commit identifier for each 
  commit.
 
  When you click on the middle button, you'll see all of the changes that were made in that 
  particular commit. Green shaded lines indicate additions and red ones removals. In the shell we 
  can do the same thing with ```git diff```. In particular, ```git diff ID1..ID2``` where ID1 and 
  ID2 are commit identifiers (e.g. ```git diff a3bf1e5..041e637```) will show the differences 
  between those two commits.
 
  The right-most button lets you view all of the files in the repository at the time of that 
  commit. To do this in the shell, we'd need to checkout the repository at that particular time. 
  We can do this with ```git checkout ID``` where ID is the identifier of the commit we want to 
  look at. If we do this, we need to remember to put the repository back to the right state 
  afterwards!
{{% /expand %}}

{{% notice note %}}
## Uploading files directly in GitHub browser

 Github also allows you to skip the command line and upload files directly to 
 your repository without having to leave the browser. There are two options. 
 First you can click the "Upload files" button in the toolbar at the top of the
 file tree. Or, you can drag and drop files from your desktop onto the file 
 tree. You can read more about this [on this GitHub page](https://help.github.com/articles/adding-a-file-to-a-repository/)
{{% /notice %}}


## GitHub Timestamp

 Create a remote repository on GitHub. Push the contents of your local
 repository to the remote. Make changes to your local repository and push these
 changes. Go to the repo you just created on GitHub and check the
 [timestamps]({{ page.root }}{% link reference.md %}#timestamp) of the files. How does GitHub
 record times, and why?

{{% expand "Solution" %}}
## Solution
  GitHub displays timestamps in a human readable relative format (i.e. "22 hours ago" or "three 
  weeks ago"). However, if you hover over the timestamp, you can see the exact time at which the 
  last change to the file occurred.
{{% /expand %}}

## Push vs. Commit

 In this episode, we introduced the "git push" command.
 How is "git push" different from "git commit"?

{{% expand "Solution" %}}
## Solution
  When we push changes, we're interacting with a remote repository to update it with the changes 
  we've made locally (often this corresponds to sharing the changes we've made with others). 
  Commit only updates your local repository.
{{% /expand %}}

## GitHub License and README files

 In this episode we learned about creating a remote repository on GitHub, but when you initialized 
 your GitHub repo, you didn't add a README.md or a license file. If you had, what do you think 
 would have happened when you tried to link your local and remote repositories?

{{% expand "Solution" %}}
## Solution
  In this case, we'd see a merge conflict due to unrelated histories. When GitHub creates a 
  README.md file, it performs a commit in the remote repository. When you try to pull the remote 
  repository to your local repository, Git detects that they have histories that do not share a 
  common origin and refuses to merge.
  ```Bash
  $ git pull origin main
  ```
{{% /expand %}}
  
 
  ```
  warning: no common commits
  remote: Enumerating objects: 3, done.
  remote: Counting objects: 100% (3/3), done.
  remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
  Unpacking objects: 100% (3/3), done.
  From https://github.com/vlad/planets
   * branch            main     - FETCH_HEAD
   * [new branch]      main     - origin/main
  fatal: refusing to merge unrelated histories
  ```
  
 
  You can force git to merge the two repositories with the option `--allow-unrelated-histories`. 
  Be careful when you use this option and carefully examine the contents of local and remote 
  repositories before merging.
  ```
  $ git pull --allow-unrelated-histories origin main
  ```
  
 
  ```
  From https://github.com/vlad/planets
   * branch            main     - FETCH_HEAD
  Merge made by the 'recursive' strategy.
  README.md | 1 +
  1 file changed, 1 insertion(+)
  create mode 100644 README.md
  ```
  
 
 {: .solution}
{: .challenge}
