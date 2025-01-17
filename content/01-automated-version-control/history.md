+++
title = "b. A slightly longer history"
weight = 2
chapter = false
+++

## The Long History of Version Control Systems

Automated version control systems are nothing new.
Tools like RCS, CVS, or Subversion have been around since the early 1980s and are used by 
many large companies.
However, many of these are now considered legacy systems (i.e., outdated) due to various 
limitations in their capabilities.
More modern systems, such as Git and [Mercurial](https://swcarpentry.github.io/hg-novice/),
are *distributed*, meaning that they do not need a centralized server to host the repository.
These modern systems also include powerful merging tools that make it possible for 
multiple authors to work on
the same files concurrently.

> ## Paper Writing
>
> *   Imagine you drafted an excellent paragraph for a paper you are writing, but later ruin 
>     it. How would you retrieve the *excellent* version of your conclusion? Is it even possible?
>
> *   Imagine you have 5 co-authors. How would you manage the changes and comments 
>     they make to your paper?  If you use LibreOffice Writer or Microsoft Word, what happens if 
>     you accept changes made using the `Track Changes` option? Do you have a 
>     history of those changes?
>
>

*   Recovering the excellent version is only possible if you created a copy
    of the old version of the paper. The danger of losing good versions
    often leads to the problematic workflow illustrated in the PhD Comics
    cartoon at the top of this page.
    
*   Collaborative writing with traditional word processors is cumbersome.
   Either every collaborator has to work on a document sequentially
   (slowing down the process of writing), or you have to send out a
   version to all collaborators and manually merge their comments into
   your document. The 'track changes' or 'record changes' option can
   highlight changes for you and simplifies merging, but as soon as you
   accept changes you will lose their history. You will then no longer
   know who suggested that change, why it was suggested, or when it was
   merged into the rest of the document. Even online word processors like
   Google Docs or Microsoft Office Online do not fully resolve these
   problems.
