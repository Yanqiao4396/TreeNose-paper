# LaTeX Repository for Writing New Papers

This repository is designed to be forked by PhD students when they want to start
writing a new research paper for a conference, journal, or an internal report.

It provides a skeleton set of files and folders in which you can write your own
material, and customise your paper with additional macros.

Each section provides advice as to how to go about writing it. This advice can
be deleted or commented out to make way for your own content.

## Create a Repository for Your Own Paper by Forking This One

In the top-right hand corner of the GitHub page for the repository, there should
be a button named "Fork". Click this to fork the repository into your own space.

The new repository will still be called "new-paper", which you will want to
change. To do this, go the "Settings" tab and rename it. Choose a name that is
indicative of the paper's *research content*, rather than the conference venue
or journal you intend to submit it to. For example, "search-based-testability"
is a better name than "icse2020".

For the same reasons as those
[detailed in the next section](#file-and-directory-naming), choose a name formatted
in "kebab-case" (i.e., all lower case with hyphens as word separators).

## Building Your Paper

I suggest you set up a development environment similar to one that you'd use for
developing software, but which will automatically compile your LaTeX and build
a PDF.

There are plenty of tools around to assist you in this process, and I have used
a number over the years. Currently, I use [Visual Studio
Code](https://code.visualstudio.com/) (VS Code for short), which is free and
open source, with the [LaTeX
workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
plugin. Among other things this plugin automatically builds my PDF every time I
make a change to a `.tex` source file. With VS Code, I can display the PDF in an
editor tab so that I can see it while I am working on it, and have it update
while I edit it. Others prefer more "traditional" solutions such as Vim or
Emacs, but you can use whatever you prefer, and so long as you do not [add any
settings or backup files produced by your editor to the
repository](#what-to-exclude-from-your-paper-repository), your personal choice
can co-exist alongside that of mine and your collaborators.

Whatever environment you use, ensure you have a spell checker installed! (Again,
VS Code has a plugin for one of these.) You will also find various other plugins
useful, for example those that manage tabs/spaces and remove trailing spaces in
your source text files.

At some point, however, you may need to compile the paper from a terminal window
The root file is `paper.tex`, and typically you will need to run LaTeX and
BibTeX a couple of times to resolve all of the references properly in the
document:

```
pdflatex paper.pdf
bibtex *.aux
pdflatex paper.pdf
pdflatex paper.pdf
```

## File and Directory Naming

Over time, you will be adding your own files and content to your paper. The
various files and examples in this repository demonstrate how to go about doing
that.

Please ensure you stick to the coding standards described in the comments of the
paper. This helps ensure everything is consistent, that other people working
with you (i.e., me, and possibly other collaborators) can find things easily (such as a
figure file referenced using a certain label in a section file), and in general
helps uphold the [Principle of Least
Surprise](https://en.wikipedia.org/wiki/Principle_of_least_astonishment)
for others when working on the paper.

In particular, the repository opts to use
"[kebab-case](https://wiki.c2.com/?KebabCase)" for naming files and directories.
All file and directory names following the kebab-case convention are
lower-cased, with words separated with hyphens. Using lower-casing and not using
spaces (i.e., by using hyphens instead) in file and directory names ensures good
cross-platform compatibility.

## What to Exclude From Your Paper Repository

You can exclude files from the repository using the provided `.gitignore`file as
a starting point. This file lives in the repository's root directory.

Firstly, do not commit build files to the repository, in particular the target
PDF file (`paper.pdf`). You should also avoid commiting:

* Temporary build files that LaTeX and BibTeX produce (e.g., `paper.aux`, etc.)

* Operating system files (e.g., `.DS_Store` on Mac) that can be particularly.
  irritating for users of other systems.

* Editor backup files (e.g., `.bak` files), and editor settings files if you can
  avoid them (e.g., `.vscode`).

### Experimental Materials

You should use a separate Git repository for all of your experimental data
and materials. That is, keep your paper repository for LaTeX files only,
or graphics/TikZ files etc. that are directly involved in the production
of your paper.

If the build of your paper needs to generate tables or figures from your raw
data, consider including it in the paper repository as a separate
[Git submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
instead. A Git submodule is just a way of using some other Git repository in
another, but where the two repositories can still be maintained independently.

## Spelling

As I remarked earlier in these instructions, please ensure you use a spell
checker! Many text editors enable you to install a plugin so that you can
see any misspelled words while you're editing your document.

British English or American English? I'm fine with whichever, so long as
everyone working on the paper knows (and doesn't keep changing the spellings
from one version of English to another).

For some publications, particularly American journals, the publisher will
change all British spellings to American anyway (e.g. IEEE, ACM). I often
just go with American even though I'm a Brit, because the spellings are
more concise --- every character of space is important! :-)

Note that there are some words that are still used in every day British
English that have disappeared from American English. These words sound
odd and quaint to the American ear (so you may find them automatically
corrected in your paper, especially if working with an American collaborator).
Top of this list is the word "whilst". Just use "while" instead.

## Using This Repository in Conjunction with Other Latex Advice on the Web

The comments of this paper offer a number of tips on how to write good LaTeX.

There is a lot of other good advice on the web, that you should check out too.
See, the following links, for example:

* [Advice for Writing LaTeX Documents](https://github.com/dspinellis/latex-advice),
  by Diomidis Spinellis.
* [John's Small Collection of LaTeX Tips](https://john.regehr.org/latex/),
  by John Regehr.

Bear in mind that sometimes the advice given is subjective, and hence
contradictory.

Always follow the guidelines specified by this repository if there is a
conflict.

For example, this repository chooses to structure papers by splitting its
content across several files. This is because I think it is better to structure
LaTeX documents in a modular fashion, much like a computer program. This
approach will help you re-use components of your papers that you have written
when you start to work on your PhD thesis.

A common objection to doing it this way is that it makes it harder to find
specific text later. But, if you structure your files in the way this repository
suggests, finding things again should not be difficult – in fact, it should be
very easy. Furthermore, if you get really stuck, then it is not hard to use the
"Find" feature of a good text editor, so long as you include all the relevant
files in the scope of the search.
