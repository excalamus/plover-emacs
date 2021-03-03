# Plover with Emacs

This repository hosts a
[Plover](http://www.openstenoproject.org/plover/) dictionary for use
with [Emacs](https://www.gnu.org/software/emacs/).

A full explanation of each dictionary entry is here: https://excalamus.github.io/plover-emacs/

The dictionary is here:
https://github.com/excalamus/plover-emacs/blob/main/plover-emacs.json

# Contributing
## A Literate Dictionary
Using [a single source
file](https://github.com/excalamus/plover-emacs/blob/main/plover-emacs.org),
it's possible to generate [a webpage explaining each entry in a Plover
dictionary](https://excalamus.github.io/plover-emacs/).  The source
file is made with Emacs [Org mode](https://orgmode.org/).

Org mode uses a markup syntax similar to Markdown
(e.g. `=verbatim-text=`, `* header`, `[[http://address][links]]`,
etc.).  See [the Org manual](https://orgmode.org/guide/Markup.html)
for markup details.  Sections indicated by

```
#+begin_src js :tangle plover-emacs.json :exports code
#+end_src
```

are what make up the dictionary.  They are blocks of source code.

The source blocks work as follows.  First, the "js" bit tells Org to
use Javascript functionality for the section.  "Tangle" is a technical
term from literate programming.  It means to take the programming
source code which is embedded in a document and extract it into an
executable form.  A related term is "weave" which means to generate a
human readable text.

When you call `M-x org-babel-tangle` in Emacs ("babel" being the name
of a module within Org that handles programming language related
things), a new file named "plover-emacs.json" is created and all
blocks with the ":tangle plover-emacs.json" directive are appended to
it.  The ":exports code" directive indicates to the system to only
export the code within the block; don't execute it and don't display
the result of running it.  Use `C-c C-e h o` to export to HTML.

The diagram below shows how everything relates:

```
        +----- ("tangle" with "org-bable-tangle")------>  plover-emacs.json -------->  used with Plover ('executable')
        |
plover-emacs.org
        |
        +---- ("weave" with the Org export system via C-c C-e h o) -----> index.html -----> read with web browser ('human readable')
```

If it's not clear by comparing plover-emacs.org to index.html, peruse
the Org manual.
