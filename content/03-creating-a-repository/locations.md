+++
title = "b. Places for git repositories"
weight = 2
chapter = false
+++

{{% notice note %}}


 ## Places to Create Git Repositories

 Along with tracking information about planets (the project we have already created), 
 Dracula would also like to track information about moons.
 Despite Wolfman's concerns, Dracula creates a `moons` project inside his `planets` 
 project with the following sequence of commands:

 ```Bash
 $ cd ~/          # return to home directory
 $ cd planets     # go into planets directory, which is already a Git repository
 $ ls -a          # ensure the .git subdirectory is still present in the planets directory
 $ mkdir moons    # make a subdirectory planets/moons
 $ cd moons       # go into moons subdirectory
 $ git init       # make the moons subdirectory a Git repository
 $ ls -a          # ensure the .git subdirectory is present indicating we have created a new Git repository
 ```
 
{{% /notice %}}

 Is the `git init` command, run inside the `moons` subdirectory, required for 
 tracking files stored in the `moons` subdirectory?
 
{{%expand "Solution" %}} 

  No. Dracula does not need to make the `moons` subdirectory a Git repository 
  because the `planets` repository will track all files, sub-directories, and 
  subdirectory files under the `planets` directory.  Thus, in order to track 
  all information about moons, Dracula only needed to add the `moons` subdirectory
  to the `planets` directory.
  
  Additionally, Git repositories can interfere with each other if they are "nested":
  the outer repository will try to version-control
  the inner repository. Therefore, it's best to create each new Git
  repository in a separate directory. To be sure that there is no conflicting
  repository in the directory, check the output of `git status`. If it looks
  like the following, you are good to go to create a new repository as shown
  above:
 
  ```Bash
  $ git status
  ```
  
  ```
  fatal: Not a git repository (or any of the parent directories): .git
  ```
{{% /expand %}}

