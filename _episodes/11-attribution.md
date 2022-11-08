---
title: Attribution
teaching: 10
exercises: 0
questions:
- "How can I get proper attribution and credit for my work"
- "What licensing information should I include with my work?"
- "How can I make my work easier to cite?"
objectives:
- "Explain why adding licensing information to a repository is important."
- "Choose a proper license."
- "Explain differences in licensing and social expectations."
- "Make your work easy to cite"
keypoints:
- "The `LICENSE`, `LICENSE.md`, or `LICENSE.txt` file is often used in a repository to indicate how the contents of the repo may be used by others."
- "People who incorporate General Public License (GPL'd) software into their own software must make their software also open under the GPL license; most other open licenses do not require this."
- "The Creative Commons family of licenses allow people to mix and match requirements and restrictions on attribution, creation of derivative works, further sharing, and commercialization."
- "People who are not lawyers should not try to write licenses from scratch."
- "Add a CITATION file to a repository to explain how you want your work cited."
---

# Licencing

When a repository with source code, a manuscript or other creative
works becomes public, it should include a file `LICENSE` or
`LICENSE.txt` in the base directory of the repository that clearly
states under which license the content is being made available. This
is because creative works are automatically eligible for intellectual
property (and thus copyright) protection. Reusing creative works
without a license is dangerous, because the copyright holders could
sue you for copyright infringement.

A license solves this problem by granting rights to others (the
licensees) that they would otherwise not have. What rights are being
granted under which conditions differs, often only slightly, from one
license to another. In practice, a few licenses are by far the most
popular, and [choosealicense.com](https://choosealicense.com/) will
help you find a common license that suits your needs.  Important
considerations include:

* Whether you want to address patent rights.
* Whether you require people distributing derivative works to also
  distribute their source code.
* Whether the content you are licensing is source code.
* Whether you want to license the code at all.

Choosing a license that is in common use makes life easier for
contributors and users, because they are more likely to already be
familiar with the license and don't have to wade through a bunch of
jargon to decide if they're ok with it.  The [Open Source
Initiative](https://opensource.org/licenses) and [Free Software
Foundation](https://www.gnu.org/licenses/license-list.html) both
maintain lists of licenses which are good choices.

[This article][software-licensing] provides an excellent overview of
licensing and licensing options from the perspective of scientists who
also write code.

At the end of the day what matters is that there is a clear statement
as to what the license is. Also, the license is best chosen from the
get-go, even if for a repository that is not public. Pushing off the
decision only makes it more complicated later, because each time a new
collaborator starts contributing, they, too, hold copyright and will
thus need to be asked for approval once a license is chosen.

> ## Can I Use Open License?
>
> Find out whether you are allowed to apply an open license to your software.
> Can you do this unilaterally,
> or do you need permission from someone in your institution?
> If so, who?
{: .challenge}

> ## What licenses have I already accepted?
>
> Many of the software tools we use on a daily basis (including in this workshop) are
> released as open-source software. Pick a project on GitHub from the list below, or
> one of your own choosing. Find its license (usually in a file called `LICENSE` or
> `COPYING`) and talk about how it restricts your use of the software. Is it one of
> the licenses discussed in this session? How is it different?
> - [Git](https://github.com/git/git), the source-code management tool
> - [CPython](https://github.com/python/cpython), the standard implementation of the Python language
> - [Jupyter](https://github.com/jupyter), the project behind the web-based Python notebooks we'll be using
> - [EtherPad](https://github.com/ether/etherpad-lite), a real-time collaborative editor
{: .challenge}

[software-licensing]: https://doi.org/10.1371/journal.pcbi.1002598

# Citations

You may want to include a file called `CITATION` or `CITATION.txt`
that describes how to reference your project;
the [one for Software
Carpentry](https://github.com/swcarpentry/website/blob/gh-pages/CITATION)
states:

~~~
To reference Software Carpentry in publications, please cite both of the following:

Greg Wilson: "Software Carpentry: Getting Scientists to Write Better
Code by Making Them More Productive".  Computing in Science &
Engineering, Nov-Dec 2006.

Greg Wilson: "Software Carpentry: Lessons Learned". arXiv:1307.5448,
July 2013.

@article{wilson-software-carpentry-2006,
    author =  {Greg Wilson},
    title =   {Software Carpentry: Getting Scientists to Write Better Code by Making Them More Productive},
    journal = {Computing in Science \& Engineering},
    month =   {November--December},
    year =    {2006},
}

@online{wilson-software-carpentry-2013,
  author      = {Greg Wilson},
  title       = {Software Carpentry: Lessons Learned},
  version     = {1},
  date        = {2013-07-20},
  eprinttype  = {arxiv},
  eprint      = {1307.5448}
}
~~~
{: .source}

More detailed advice, and other ways to make your code citable can be found
[at the Software Sustainability Institute blog](https://www.software.ac.uk/how-cite-and-describe-software) and in:

~~~
Smith AM, Katz DS, Niemeyer KE, FORCE11 Software Citation Working Group. (2016) Software citation
principles. [PeerJ Computer Science 2:e86](https://peerj.com/articles/cs-86/)
https://doi.org/10.7717/peerj-cs.8
~~~
{: .source}


There is also an [`@software{...`](https://www.google.com/search?q=git+citation+%22%40software%7B%22)
[BibTeX](https://www.ctan.org/pkg/bibtex) entry type in case
no "umbrella" citation like a paper or book exists for the project you want to
make citable.
