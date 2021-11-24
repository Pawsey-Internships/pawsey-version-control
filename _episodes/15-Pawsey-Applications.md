---
title: Introduction to Applications within Pawsey
teaching: 15
exercises: 0
questions:
- "How can I apply version control to file transfer and file management between my local and Pawsey systems?"
objectives:
- "Understand how to apply version control to you Pawsey project."
- "Understand why you would want to use version control in your project."
keypoints:
- "Version control enhances project file management."
---

As soon as people can work in parallel, they'll likely step on each other's
toes.  This will even happen with a single person: if we are working on
a piece of software on both our laptop and a server in the lab, we could make
different changes to each copy.  Version control helps us manage these
[conflicts]({{ page.root}}{% link reference.md %}#conflict) by giving us tools to
[resolve]({{ page.root }}{% link reference.md %}#resolve) overlapping changes.

To see how we can resolve conflicts, we must first create one.  The file
`mars.txt` currently looks like this in both partners' copies of our `planets`
repository:

~~~
$ cat mars.txt
~~~
{: .language-bash}

~~~
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
~~~
{: .output}

Let's add a line to the collaborator's copy only:

~~~
$ nano mars.txt
$ cat mars.txt
~~~
{: .language-bash}

~~~
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line added to Wolfman's copy
~~~
{: .output}

and then push the change to GitHub:

~~~
$ git add mars.txt
$ git commit -m "Add a line in our home copy"
~~~
{: .language-bash}