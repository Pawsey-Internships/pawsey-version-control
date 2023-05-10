+++
title = "f. Directories"
weight = 2
chapter = false
+++


 Two important facts you should know about directories in Git.

 1. Git does not track directories on their own, only files within them.
    Try it for yourself:

    ```Bash
    $ mkdir spaceships
    $ git status
    $ git add spaceships
    $ git status
    ```
    

    Note, our newly created empty directory `spaceships` does not appear in
    the list of untracked files even if we explicitly add it (_via_ `git add`) to our
    repository. This is the reason why you will sometimes see `.gitkeep` files
    in otherwise empty directories. Unlike `.gitignore`, these files are not special
    and their sole purpose is to populate a directory so that Git adds it to
    the repository. In fact, you can name such files anything you like.

 2. If you create a directory in your Git repository and populate it with files,
    you can add all files in the directory at once by:

    ```Bash
    git add <directory-with-files
    ```
    

    Try it for yourself:

    ```
    $ touch spaceships/apollo-11 spaceships/sputnik-1
    $ git status
    $ git add spaceships
    $ git status
    ```
    

    Before moving on, we will commit these changes.

    ```Bash
    $ git commit -m "Add some initial thoughts on spaceships"
    ```
    

To recap, when we want to add changes to our repository,
we first need to add the changed files to the staging area
(`git add`) and then commit the staged changes to the
repository (`git commit`):

![The Git Commit Workflow](images/git-committing.svg)
