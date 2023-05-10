+++
title = "g. Exercises"
weight = 2
chapter = false
+++

## Exercise: Choosing a Commit Message

 Which of the following commit messages would be most appropriate for the
 last commit made to `mars.txt`?

 1. "Changes"
 2. "Added line 'But the Mummy will appreciate the lack of humidity' to mars.txt"
 3. "Discuss effects of Mars' climate on the Mummy"


{{% expand "Solution" %}}
  Answer 1 is not descriptive enough, and the purpose of the commit is unclear;
  and answer 2 is redundant to using "git diff" to see what changed in this commit;
  but answer 3 is good: short, descriptive, and imperative.

{{% /expand %}}

## Exercise: Committing Changes to Git

 Which command(s) below would save the changes of `myfile.txt`
 to my local Git repository?

 1. ```Bash
    $ git commit -m "my recent changes"
    ```
    
 2. ```Bash
    $ git init myfile.txt
    $ git commit -m "my recent changes"
    ```
    
 3. ```Bash
    $ git add myfile.txt
    $ git commit -m "my recent changes"
    ```
    
 4. ```Bash
    $ git commit -m myfile.txt "my recent changes"
    ```
    
{{% expand "Solution" %}}
 
  1. Would only create a commit if files have already been staged.
  2. Would try to create a new repository.
  3. Is correct: first add the file to the staging area, then commit.
  4. Would try to commit a file "my recent changes" with the message myfile.txt.

{{% /expand %}}

## Exercise: Committing Multiple Files

 The staging area can hold changes from any number of files
 that you want to commit as a single snapshot.

 1. Add some text to `mars.txt` noting your decision
 to consider Venus as a base
 2. Create a new file `venus.txt` with your initial thoughts
 about Venus as a base for you and your friends
 3. Add changes from both files to the staging area,
 and commit those changes.

{{% expand "Solution" %}}
 
  First we make our changes to the `mars.txt` and `venus.txt` files:
  ```Bash
  $ nano mars.txt
  $ cat mars.txt
  ```
  
  ```
  Maybe I should start with a base on Venus.
  ```
  
  ```Bash
  $ nano venus.txt
  $ cat venus.txt
  ```
  
  ```
  Venus is a nice planet and I definitely should consider it as a base.
  ```
  
  Now you can add both files to the staging area. We can do that in one line:
 
  ```Bash
  $ git add mars.txt venus.txt
  ```
  
  Or with multiple commands:
  ```Bash
  $ git add mars.txt
  $ git add venus.txt
  ```
  
  Now the files are ready to commit. You can check that using `git status`. If you are ready to commit use:
  ```Bash
  $ git commit -m "Write plans to start a base on Venus"
  ```
  
  ```
  [main cc127c2]
   Write plans to start a base on Venus
   2 files changed, 2 insertions(+)
   create mode 100644 venus.txt
  ```
{{% /expand %}}

## Exercise: `bio` Repository

 * Create a new Git repository on your computer called `bio`.
 * Write a three-line biography for yourself in a file called `me.txt`,
 commit your changes
 * Modify one line, add a fourth line
 * Display the differences
 between its updated state and its original state.

{{% expand "Solution" %}} 
  If needed, move out of the `planets` folder:
 
  ```Bash
  $ cd ..
  ```
  
 
  Create a new folder called `bio` and 'move' into it:
 
  ```Bash
  $ mkdir bio
  $ cd bio
  ```
  
 
  Initialise git:
 
  ```Bash
  $ git init
  ```
  
 
  Create your biography file `me.txt` using `nano` or another text editor.
  Once in place, add and commit it to the repository:
 
  ```Bash
  $ git add me.txt
  $ git commit -m "Add biography file" 
  ```
  
 
  Modify the file as described (modify one line, add a fourth line).
  To display the differences
  between its updated state and its original state, use `git diff`:
 
  ```Bash
  $ git diff me.txt
  ```
 {{% /expand %}} 
 

[commit-messages]: https://chris.beams.io/posts/git-commit/
[git-references]: https://git-scm.com/book/en/v2/Git-Internals-Git-References

