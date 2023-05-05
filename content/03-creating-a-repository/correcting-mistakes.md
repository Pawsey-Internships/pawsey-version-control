+++
title = "c. Correcting git init mistakes"
weight = 2
chapter = false
+++

{{% notice note %}}
 ## Correcting `git init` Mistakes
 Wolfman explains to Dracula how a nested repository is redundant and may cause confusion
 down the road. Dracula would like to remove the nested repository.
 

{{% /notice %}}

 How can Dracula undo 
 his last `git init` in the `moons` subdirectory?

{{%expand "Solution" %}}
  ## Solution -- USE WITH CAUTION!
 
  ### Background
  Removing files from a Git repository needs to be done with caution. But we have not learned 
  yet how to tell Git to track a particular file; we will learn this in the next episode. Files 
  that are not tracked by Git can easily be removed like any other "ordinary" files with
  ```
  $ rm filename
  ```
  
 
  Similarly a directory can be removed using `rm -r dirname` or `rm -rf dirname`.
  If the files or folder being removed in this fashion are tracked by Git, then their removal 
  becomes another change that we will need to track, as we will see in the next episode.
 
  Git keeps all of its files in the `.git` directory.
  To recover from this little mistake, Dracula can just remove the `.git`
  folder in the moons subdirectory by running the following command from inside the `planets` directory:
 
  ```
  $ rm -rf moons/.git
  ```

 {{% /expand %}} 
 
  But be careful! Running this command in the wrong directory will remove
  the entire Git history of a project you might want to keep.
  Therefore, always check your current directory using the command `pwd`.
