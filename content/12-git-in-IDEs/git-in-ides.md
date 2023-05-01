+++
title = "a. Git in IDE's"
weight = 2
chapter = true
+++
 
# Using git in and Integrated Development Environment (Visual Studio Code)

An integrated development environment (IDE) is software for building applications 
that combines common developer tools into a single graphical user interface (GUI). 
An IDE typically consists of a code editor, some form of build automation and a debugger. 

An IDE allows developers to start programming new applications quickly because multiple utilities 
don’t need to be manually configured and integrated as part of the setup process. 
Developers also don’t need to spend hours individually learning how to use different tools when every utility is represented in the same workbench.
Version control is another tool that can be very useful when developing code and most IDE's have some visual interface to it.

[Visual Studio Code ](https://code.visualstudio.com/) is currently the most popular
IDE. It has support for almost all popular programming languages and great
integration with Git. While some advanced Git features still require the
command-line, VS-Code has a nice interface for many common Git operations.

start by opening our existing planets folder in VS-Code:

![VS-Code screenshot showing the file menu dropdown with "New Project..." selected](images/vscode-file-selection.png)

This will open a dialog asking us what folder we want to open.
Simply navigate to the directory we just created and click open.

VS-Code will then ask us whether to enable all the editor features or not.
As we have created this workspace we should click yes. If you are opening an 
existing project/workspace consider first if there are any security risks before 
doing so.

![VS-Code screenshot showing how to enable all editor features](images/vscode-enable-trust.png)

Ta-da! We have created a new project in VS-Code within the existing planets
repository. 

Lets add some content to `pluto.txt`and save with `Ctrl+s`. Notice the vertical "Git" icon menu in the menu bar. 
VS Code has git support by default we simply need to go to the git tab:

![VS-Code screenshot showing location of git tab](images/vscode-git-extension.png)

Clicking on this icon will bring up a different menu in VS-Code. 

{{% notice note %}}
## New Repositories
 
 If this were a completely new project with no git repo we would have to initalise one.
 VS-Code makes this simple by having a single click button:
 ![VS-Code screenshot showing how to initialise a repository](images/vscode-initialise-repository.png)
{{% /notice %}}

To stage a file simply mouse over the 
change and click the plus icon:

![VS-Code screenshot showing how to stage a change](images/vscode-add-file.png)

To unstage this change we can simply click the minus button on in the staged changes section.
But if we are happy and want to commit the change we simply need to enter a message and click 
the commit button:

![VS-Code screenshot showing how to commit a change](images/vscode-commit.png)

The changes can be pushed by selecting "Push Branch" from the Git menu. There
are also options to pull from the remote repository, and to view the commit
history:

![VS-Code screenshot showing the git menu dropdown with "History" selected](images/vscode-history.png)


To push this to our remote repository we just need to click the sync button. 
Depending on what branch you are on it might be a circular icon or a cloud icon.
One means it will sync changes with github the other means it will push up the new branch.

![VS-Code screenshot showing how to push changes to a remote](images/vscode-push.png)



In the git tab, if we click on "Commits", we can see a graphical version of what `git log`
would tell us.

We can change branches or create new ones by clicking on the branch icon near the bottom of 
the window:

![VS-Code screenshot showing how to change branches](images/vscode-branch.png)


 ## Challenge

 1. Create a new file in your project.
 2. Stage this file and commit it using VS-Code's interface

{{% expand "Solution" %}}
  ## Solution to Challenge
 
  See the screenshots on how to add a file. In the history section 
  You should see another commit 
 {{% /expand %}} 

There are many more features in the VS-Code Git menu, but these should be
enough to get you started!
