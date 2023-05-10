+++
title = "a. Open Science"
weight = 2
chapter = true
+++

    The opposite of "open" isn't "closed".
    The opposite of "open" is "broken".

 --- John Wilbanks

Free sharing of information might be the ideal in science,
but publication practices sometimes make this difficult. Typically, journals don't 
require authors to submit their code, and only some require the actual data used in 
a paper. Add to that the fact that many papers sit behind a paywall and all of a sudden
the information doesn't seem so open.

However, a growing number of scientists are making use of <b open access repositories </b
to share every element of their publication, from the paper, to the code, to the data. Now,
a truly open workflow might look something like this:

*   The data is stored in an open access repository
    like [figshare](https://figshare.com/) or
    [Zenodo](https://zenodo.org), possibly as soon as it's collected,
    and given its own
    [Digital Object Identifier](https://en.wikipedia.org/wiki/Digital_object_identifier) (DOI).
    Or the data was already published and is stored in
    [Dryad](https://datadryad.org/).
*   Code (and potentiall some output) is stored in a dedicated repository on [GitHub](https://github.com), 
    [Bitbucket](https://bitbucket.org) or similar, which is kept up to date throughout the analysis process.
*   The paper draft is also kept in a <bprivate</b repository, or, if using LaTeX, on [Overleaf](https://www.overleaf.com/), 
    so that there is a hub for collaboration with colleagues and co-authors.
*   When the paper is ready, it is posted to a preprint server like [arXiv](https://arxiv.org/), 
    and also submitted it to a journal of choice.
*   The published paper includes links to the preprint, code and data repositories,
    which  makes it much easier for other scientists
    to use the work as starting point for their own research.


This open model accelerates discovery:
the more open work is,
[the more widely it is cited and re-used](https://doi.org/10.1371/journal.pone.0000308).
However,
people who want to work this way need to make some decisions
about what exactly "open" means and how to do it. You can find more on the different aspects of Open Science in [this book](https://link.springer.com/book/10.1007/978-3-319-00026-8).

This is one of the (many) reasons we teach version control.
When used diligently,
it answers the "how" question
by acting as a shareable electronic lab notebook for computational work:

*   The conceptual stages of your work are documented, including who did
    what and when. Every step is stamped with an identifier (the commit ID)
    that is for most intents and purposes unique.
*   You can tie documentation of rationale, ideas, and other
    intellectual work directly to the changes that spring from them.
*   You can refer to what you used in your research to obtain your
    computational results in a way that is unique and recoverable.
*   With a version control system such as Git, 
    the entire history of the repository is easy to archive for perpetuity.
    
{{% notice note %}} 
 ## Work in progress & Pawsey projects

 It is often a good idea to start out with a private repository for code and/or data that
 is a work in progress (e.g. your data is still being collected, your code is only half 
 finished) to prevent the unintended use of your research. We covered the difference between
 public and private repositories in the previous github lesson
 
 If you are unsure about how to begin with your Pawsey project, start with private repositories
 and you can always make a public fork later on. Don't forget to chat to your supervisors
 about this too!
{{% /notice %}}

{{% notice note %}}
 ## Making Code Citable

 Anything that is hosted in a version control repository (data, code, papers, 
 etc.) can be turned into a citable object. 
{{% /notice %}}

{{% notice note %}}
 ## Preprint servers

 Preprint servers like [arXiv](https://arxiv.org/) are now a popular way for researchers
 to share their papers freely with the academic community. In some cases these are even
 replacing traditional, subscription-based journals. If you're at the stage of publishing a
 paper though, be sure to check the guidelines of the journal you want to submit to, and 
 ask around in your discipline to find out whether there are any restrictions on when and
 how you submit to a preprint server.
{{% /notice %}}
