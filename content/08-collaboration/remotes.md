+++
title = "a. Collaborating"
weight = 2
chapter = false
+++

Now most of you are going to be working on <bSetonix</b or <bTopaz</b,
but from time to time you may want to develop scripts or work on your projects on
your local machine. Here, we're going to see how you can use version control to 
set up a multi-machine workflow to efficiently transfer your work between your own
machine and Pawsey systems.

Some of the steps here should be revision from previous lessons, so try to do as much
as you can without looking at the answers!

First, you'll need to ssh into Setonix and change into your scratch
directory, as this is where we want to put `planets`. (Instead of `pawsey_username` here
you should use the Pawsey training account you were given yesterday).

```Bash
$ ssh pawsey_username@setonix.pawsey.org.au
$ cd $MYSCRATCH
```


Next you'll need to go through the process of setting up a public-private pair
again like we did on your local machine, and copying it to your [GitHub account](https://github.com/settings/keys) 
(don't forget to note down the passphrase you choose at the prompt!):

{{% expand "Hint" %}}
 ## Hint
 Remember once you have set it up, you can find the public key to copy over here:
 ```Bash
 $ cat ~/.ssh/id_ed25519.pub
 ```
 
 
 
 And you can check that the connection is successful like so:
 ```Bash
 $ ssh -T git@github.com
 ```
 

 ```
 Hi usernameXXXX! You've successfully authenticated, but GitHub does not provide shell access.
 
 ```
{{% /expand %}} 

{{% expand "Solution" %}}
## Solution
To create a key on Setonix you would use the command:
 ```
 $ ssh-keygen -t ed25519 -C "github-account-email@gmail.com"
 ```
{{% /expand %}}

Then, we'll make a copy of the entire remote repository on Setonix
using a process called "cloning a repo". `git clone` (don't forge to change 
username to your own!):

```Bash
$ git clone git@github.com:username/planets.git
$ cd planets
``` 



Now we're ready to make some changes to the repository, let's add a new file:

```Bash
$ touch pawsey_planets.txt
$ git add pawsey_planets.txt
$ git commit -m "created pawsey_planets.txt"
```


Then push our changes back to the remote repository.

```Bash
$ git push origin main
```


``` 
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 32 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 229 bytes | 229.00 KiB/s, done.
Total 2 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:username/planets.git
   6c8fdc4..f55eca8  main - main
```


Note that we didn't have to create a remote called `origin`: Git uses this
name by default when we clone a repository.  (This is why `origin` was a
sensible choice earlier when we were setting up remotes by hand.)

Take a look at the repository on GitHub again, and you should be 
able to see the new commit. You may need to refresh
your browser to see the new commit.

Now, either logout of Setonix (remember you can just type `logout`), or open a new
terminal window and navigate to the `planets` directory on your local machine. Enter the `ls` command
and inspect the output. Do you see `pawsey_planets.txt`? If not, why? and what do you need to do to fix 
it?

{{% expand "Solution" %}}
 ## Solution
 No, you won't see `pawsey_planets.txt` yet because we haven't updated the repo on our local machine!
 To fix this we need to pull from the remote repository again:
 ```Bash
 $ git pull origin main
 ```
 
 After doing this you should see `pawsey_planets.txt` in your remote repository with the `ls` command.
{{% /expand %}}

And that's all there is to it! You have your `planets` directory on both your local machine and 
Setonix linked via the remote repository on GitHub, and you can easily transfer
your code/files/results between the two.

{{% notice note %}}
## GitHub and large data files

 Note that GitHub is not designed to handle large files out of the box, so make sure to 
 add any data folders to your `.gitignore` before staging any commits. If you do need some way to 
 transfer large `.md5` files or the like, check out our later lesson on [Open Science](https://pawsey-internships.github.io/version-control/10-open/index.html).
{{% /notice %}}

Now that's half the story, what if you want to share your work with your supervisor, or another
intern, so they can make some additions to your code? This is going to work much the same 
way as it does above for two machines, just this time one of the machines has another 
human at the keyboard! 

For the next step, get into pairs.  One person will be the "Owner" and the other
will be the "Collaborator". The goal is that the Collaborator add changes into
the Owner's repository. We will switch roles at the end, so both persons will
play Owner and Collaborator. Now is a good time to remind your instructor 
about setting Collaborator-Owner pairs if s/he has forgotten.
Hint: pairs.png


The Owner needs to give the Collaborator access. On GitHub, click the settings
button on the right, select Manage access, click Invite a collaborator, and
then enter your partner's username.

![Adding Collaborators on GitHub](images/github-add-collaborators.png)

To accept access to the Owner's repo, the Collaborator
needs to go to [https://github.com/notifications](https://github.com/notifications).
Once there she can accept access to the Owner's repo.

Next, the Collaborator needs to clone the Owner's repo, just like we did above.
However this time, we want to make sure we can tell the difference between our own
`planets` folder and our collaborator's. To do this, we supply the target directory
as a second argument to `git clone`:

```Bash
$ git clone git@github.com:username/planets.git ~/Desktop/partner-planets
```


If you choose to clone without the clone path
(`~/Desktop/partner-planets`) specified at the end,
you will clone inside your own planets folder!
Make sure to navigate to the `Desktop` folder first.

![After Creating Clone of Repository](images/github-collaboration.svg)

The Collaborator can now make a change in her clone of the Owner's repository,
exactly the same way as we've been doing before. Try something out! You'll need 
to make some changes, <istage</i those changes with `git add`, commit them with
`git commit` (don't forget to add a commit message) and finally <ipush</i the 
commit.

{{% notice note %}}
## Solution
 Your process might look something like this:
 
 ```Bash
 $ cd ~/Desktop/vlad-planets
 $ nano pluto.txt
 $ cat pluto.txt
 ```
 

 ```
 It is so a planet!
 ```
 

 ```Bash
 $ git add pluto.txt
 $ git commit -m "Add notes about Pluto"
 ```
 
 
 ```Bash
  1 file changed, 1 insertion(+)
  create mode 100644 pluto.txt
 ```
{{% /notice %}} 


Then push the change to the *Owner's repository* on GitHub:

```
$ git push origin main
```


```
Enumerating objects: 4, done.
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 306 bytes, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/vlad/planets.git
   9272da5..29aba7c  main - main
```


Check your own repo on GitHub to prove to yourself that you haven't made any changes 
there. 
