+++
title = "c. Default branching"
weight = 2
chapter = false
+++

Git (2.28+) allows configuration of the name of the branch created when you
initialize any new repository.  Dracula decides to use that feature to set it to `main` so 
it matches the cloud service he will eventually use. 

```Bash
$ git config --global init.defaultBranch main
```

> ## Default Git branch naming
>
> Source file changes are associated with a "branch." 
> For new learners in this lesson, it's enough to know that branches exist, and this lesson uses one branch.  
> By default, Git will create a branch called `master` 
> when you create a new repository with `git init` (as explained in the next Episode). This term evokes 
> the racist practice of human slavery and the 
> [software development community](https://github.com/github/renaming)  has moved to adopt 
> more inclusive language. 
> 
> In 2020, most Git code hosting services transitioned to using `main` as the default 
> branch. As an example, any new repository that is opened in GitHub and GitLab default 
> to `main`.  However, Git has not yet made the same change.  As a result, local repositories 
> must be manually configured have the same main branch name as most cloud services.  
> 
> For versions of Git prior to 2.28, the change can be made on an individual repository level.  The 
> command for this is in the next episode.  Note that if this value is unset in your local Git 
> configuration, the `init.defaultBranch` value defaults to `master`.
>
{: .callout}

The five commands we just ran above only need to be run once: the flag `--global` tells Git
to use the settings for every project, in your user account, on this computer.

You can check your settings at any time:

```Bash
$ git config --list
```
