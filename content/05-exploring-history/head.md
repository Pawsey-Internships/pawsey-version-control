+++
title = "c. Head"
weight = 2
chapter = false
+++

 ## Don't Lose Your HEAD

 Above we used

 ```
 $ git checkout f22b25e mars.txt
 ```
 

 to revert `mars.txt` to its state after the commit `f22b25e`. But be careful! 
 The command `checkout` has other important functionalities and Git will misunderstand
 your intentions if you are not accurate with the typing. For example, 
 if you forget `mars.txt` in the previous command.

 ```
 $ git checkout f22b25e
 ```
 
 ```
 Note: checking out 'f22b25e'.

 You are in 'detached HEAD' state. You can look around, make experimental
 changes and commit them, and you can discard any commits you make in this
 state without impacting any branches by performing another checkout.

 If you want to create a new branch to retain commits you create, you may
 do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name

 HEAD is now at f22b25e Start notes on Mars as a base
 ```

 The "detached HEAD" is like "look, but don't touch" here,
 so you shouldn't make any changes in this state.
 After investigating your repo's past state, reattach your `HEAD` with `git checkout main`.
