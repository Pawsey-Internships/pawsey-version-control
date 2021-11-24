---
title: Introduction to Pawsey Project Applications
teaching: 15
exercises: 0
questions:
- "How can I apply version control to file transfer and file management between my local and Pawsey systems?"
objectives:
- "Understand how to apply version control to you Pawsey project."
- "Understand why you would want to use version control in your project."
keypoints:
- "Version control enhances project file management."
---

Here we will demonstrate with a quick exercise to serve as both reinforcement for 
the introduction to supercomputing session and as a pairing withn the version control 
training to showcase the introductory capabilities of Git for your project.

For the first step, please create a private repository in your GitHub.com account through
the Browser interface. Name this private repo "test-vc"

~~~
$ ssh username@zeus.pawsey.org.au
$ cd $MYSCRATCH
$ ls
~~~
{: .language-bash}

~~~
Introductory-Supercomputing
~~~
{: .output}

If you don't see the above output, you can clone directory with 
`git clone https://github.com/PawseySC/Introductory-Supercomputing.git`.

Let's change from the PawseySC account remote repository to our 
own newly created private repo. Replace "username" with your 
GitHub account username.

~~~
$ cd Introductory-Supercomputing
$ git remote rm origin
$ git remote -v
$ git remote add origin git@github.com:username/test-vc.git
$ git remote -v
~~~
{: .language-bash}

~~~
origin	git@github.com:username/test-vc.git (fetch)
origin	git@github.com:username/test-vc.git (push)
~~~
{: .output}

Now, then push the change to GitHub:

~~~
$ git add .
$ git commit -m "First commit"
~~~
{: .language-bash}

~~~
[master 4dda526] first commit to private repo
 Committer: Course XXX Account <XXXYYY@zeus-1.pawsey.org.au>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 1 insertion(+), 1 deletion(-)
 ~~~
{: .output}

~~~
$ git checkout -b main
~~~
{: .language-bash}

~~~
$ ssh-keygen -t ed25519 -C "github-account-email@gmail.com"
~~~
{: .language-bash}

1. Now press enter for the default file.
2. Enter a passphrase twice and note it down.

~~~
$ cat ~/.ssh/id_ed25519.pub
~~~
{: .language-bash}

Copy the contents of the output and add to new SSH key in your GitHub account
through Browser interface. Once complete the process as per Section 7 - Remotes
 in GitHub:

~~~
$ ssh -T git@github.com
~~~
{: .language-bash}

~~~
Hi bjornXXXXX! You've successfully authenticated, but GitHub does not provide shell access.

~~~
{: .output}

~~~
$ git push origin main
~~~
{: .language-bash}

~~~
XXXYYY@zeus-1:/scratch/coursesXX/XXXYYY/Introductory-Supercomputing> git push origin main
Counting objects: 50, done.
Delta compression using up to 20 threads.
Compressing objects: 100% (47/47), done.
Writing objects: 100% (50/50), 206.49 KiB | 0 bytes/s, done.
Total 50 (delta 14), reused 0 (delta 0)
remote: Resolving deltas: 100% (14/14), done.
To github.com:bjornXXXXXX/test-vc.git
 * [new branch]      main -> main
~~~
{: .output}

Now we can refresh our GitHub "test-vc" repository page and inspect the files and directories that
have been push to our private repository.

To close out, we'll try clone the repository to our home directories on our local machines,
make an edit, push to the remote repository, and lastly pull the change to our local repository
on Zeus. Completing this, we are simulating a potential workflow with version control for our
projects this Summer.

> ## Six Effective Git Commands to Own Your Workflow 
>
> Great way to work with multiple branches:
> * `git stash` stash your local changes
> * `git pull origin main` Update the branch with the most recent code.
> * `git stash apply` Merge your local changes with the most recent code.
> * `git add .` Add your changes.
> * `git commit -m "Informative and memorable short message"` Commit your changes.
> * `git push origin main` Push your changes.
{: .callout}

