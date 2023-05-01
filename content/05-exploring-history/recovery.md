+++
title = "e. recovery"
weight = 2
chapter = false
+++

It's important to remember that
we must use the commit number that identifies the state of the repository
*before* the change we're trying to undo.
A common mistake is to use the number of
the commit in which we made the change we're trying to discard.
In the example below, we want to retrieve the state from before the most
recent commit (`HEAD~1`), which is commit `f22b25e`:

![Git Checkout](images/git-checkout.svg)

So, to put it all together,
here's how Git works in cartoon form:

![https://figshare.com/articles/How_Git_works_a_cartoon/1328266](images/git_staging.svg)

{{% notice note %}}
 ## Simplifying the Common Case

 If you read the output of `git status` carefully,
 you'll see that it includes this hint:

 ```
 (use "git checkout -- <file..." to discard changes in working directory)
 ```

 As it says,
 `git checkout` without a version identifier restores files to the state saved in `HEAD`.
 The double dash `--` is needed to separate the names of the files being recovered
 from the command itself:
 without it,
 Git would try to use the name of the file as the commit identifier.
{{% /notice %}}

The fact that files can be reverted one by one
tends to change the way people organize their work.
If everything is in one large document,
it's hard (but not impossible) to undo changes to the introduction
without also undoing changes made later to the conclusion.
If the introduction and conclusion are stored in separate files,
on the other hand,
moving backward and forward in time becomes much easier.

