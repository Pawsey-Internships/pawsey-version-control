+++
title = "e. commit -m"
weight = 2
chapter = false
+++

 ## `git commit` without `-m`

 You might have noticed that so far we have only been using `git commit -m`
 which adds a message to our commit in a single command.
 If you forget to type `-m` or want a proper editor experience running
 `git commit` on its own will bring up an editor in your terminal and allow
 you to type out your commit message.

 What editor is brougt up will depend on your platform and what you have configured
 but you will see a file that looks like the following:
 ```Bash
 git commit
 ```
 
 ```

 # Please enter the commit message for your changes. Lines starting
 # with '#' will be ignored, and an empty message aborts the commit.
 #
 # On branch main
 # Changes to be committed:
 #   modified:   a/mars.txt
 #   modified:   b/bars.txt
 #
 ```
 
