+++
title = "a. Github"
weight = 2
chapter = false
+++

Version control really comes into its own when we begin to collaborate with
other people.  We already have most of the machinery we need to do this; the
only thing missing is to copy changes from one repository to another.

Systems like Git allow us to move work between any two repositories.  In
practice, though, it's easiest to use one copy as a central hub, and to keep it
on the web rather than on someone's laptop.  Most programmers use hosting
services like [GitHub](https://github.com), [Bitbucket](https://bitbucket.org) or
[GitLab](https://gitlab.com/) to hold those main copies; we'll explore the pros
and cons of this in a later episode.

Let's start by sharing the changes we've made to our current project with the
world.  Log in to GitHub, then click on the icon in the top right corner to
create a new repository called `planets`:

![Creating a Repository on GitHub (Step 1)](images/github-create-repo-01.png)

Name your repository "planets" and then click "Create Repository".

Note: Since this repository will be connected to a local repository, it needs to be empty. Leave 
"Initialize this repository with a README" unchecked, and keep "None" as options for both "Add 
.gitignore" and "Add a license." See the "GitHub License and README files" exercise below for a full 
explanation of why the repository needs to be empty.



![Creating a Repository on GitHub (Step 2)](images/github-create-repo-02.png)
{{% notice note %}}
 ## Public vs Private Gihub Repos

 You will notice in the above example we have selected public when creating the repository.
 As anyone can see these kinds of repositories you may not want to host sensitive code or data on them.
 Whilst you have complete control over private repos, but they cost money unless you have a github student developer
 pack.
 Make sure to carefully consider what kind of access controls you need for a project repository but don't stress as
 repos can easily be converted from private to public and vice versa.
{{% /notice %}}

As soon as the repository is created, GitHub displays a page with a URL and some
information on how to configure your local repository:

![Creating a Repository on GitHub (Step 3)](images/github-create-repo-03.png)

This effectively does the following on GitHub's servers:

```Bash
$ mkdir planets
$ cd planets
$ git init
```


If you remember back to the earlier [episode](../04-changes/) where we added and
committed our earlier work on `mars.txt`, we had a diagram of the local repository
which looked like this:

![The Local Repository with Git Staging Area](images/git-staging-area.svg)

Now that we have two repositories, we need a diagram like this:

![Freshly-Made GitHub Repository](images/git-freshly-made-github-repo.svg)

Note that our local repository still contains our earlier work on `mars.txt`, but the
remote repository on GitHub appears empty as it doesn't contain any files yet.

The next step is to connect the two repositories.  We do this by making the
GitHub repository a [remote]({{ page.root}}{% link reference.md %}#remote) for the local repository.
The home page of the repository on GitHub includes the string we need to
identify it:

![Where to Find Repository URL on GitHub](images/github-find-repo-string.png)

Click on the 'SSH' link to change the [protocol]({{ page.root }}{% link reference.md %}#protocol) from HTTPS to SSH.

{{% notice note %}}
 ## HTTPS vs. SSH

 We use SSH here because, while it requires some additional configuration, it is a 
 security protocol widely used by many applications.  The steps below describe SSH at a 
 minimum level for GitHub. A supplemental episode to this lesson discusses advanced setup 
 and concepts of SSH and key pairs, and other material supplemental to git related SSH. 
{{% /notice %}}

![Changing the Repository URL on GitHub](images/github-change-repo-string.png)

Copy that URL from the browser, go into the local `planets` repository, and run
this command:

```Bash
$ git remote add origin git@github.com:vlad/planets.git
```


Make sure to use the URL for your repository rather than Vlad's: the only
difference should be your username instead of `vlad`.

`origin` is a local name used to refer to the remote repository. It could be called
anything, but `origin` is a convention that is often used by default in git
and GitHub, so it's helpful to stick with this unless there's a reason not to.

We can check that the command has worked by running `git remote -v`:

```Bash
$ git remote -v
```


```
origin   git@github.com:vlad/planets.git (fetch)
origin   git@github.com:vlad/planets.git (push)
```


We'll discuss remotes in more detail in the next episode, while
talking about how they might be used for collaboration.

{{% notice note %}}
 ## Cloning a private repo

 If you choose to create a private repository you will need to authenticate to clone
 a repository regardless of if you chose to do so with ssh or https.
{{% /notice %}}
