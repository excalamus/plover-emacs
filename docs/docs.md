# A Literate Dictionary
With Emacs [Org mode](https://orgmode.org/), it's possible to generate
[a webpage explaining each entry in a Plover
dictionary](https://excalamus.github.io/plover-emacs/), as well as
generate the dictionary itself, using [a single source
file](https://github.com/excalamus/plover-emacs/blob/main/plover-emacs.org).

Org mode uses a markup syntax similar to Markdown
(e.g. `=verbatim-text=`, `* header`, `[[http://address][links]]`,
etc.).  See [the Org manual](https://orgmode.org/guide/Markup.html)
for markup details.  Sections indicated by

```
#+begin_src js :tangle ../plover-emacs.json :exports code
#+end_src
```

are what make up the dictionary.  They are blocks of source code.

The source blocks work as follows.  First, the "js" part tells Org to
use JavaScript functionality for the section.  "Tangle" is a technical
term from literate programming.  It means to take the programming
source code which is embedded in a document and extract it into an
executable form.  A related term is "weave" which means to generate a
human readable text.

When `M-x org-babel-tangle` is called in Emacs ("babel" being the name
of a module within Org that handles programming language related
things), a new file named "plover-emacs.json" is created and all
blocks with the ":tangle plover-emacs.json" directive are appended to
it.  This is what is meant by "tangle".  The ":exports code" directive
indicates to the system to only export the code within the block;
don't execute it and don't display the result of running it.  Use `C-c
C-e h o` to export to HTML.  The export "weaves" the document into a
publishable format.

The diagram below shows how everything relates:

```
		+----- ("tangle" with "org-bable-tangle")------>  plover-emacs.json -------->  used with Plover ('executable')
		|
plover-emacs.org
		|
		+---- ("weave" with the Org export system via C-c C-e h o) -----> index.html -----> read with web browser ('human readable')
```
