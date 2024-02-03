# Preprint Template

## Installation
This is a template for use with [copier](https://copier.readthedocs.io/en/stable/).
If you want to use this template yourself, you first need to install copier (e.g. `pip install copier`), create a new directory, change into it, and then then run
```sh
copier gh:rutar-academic/template-thesis .
```
If this template has updated and you also want to update your local template, from the root of the project folder, run
```sh
copier update
```
You might also be interested in only the project files: these can be found on the [releases page](https://github.com/rutar-academic/template-thesis/releases/latest).

## BibLaTeX
BibLaTeX is automatically loaded with a number of settings.
Notably, the [biber](https://ctan.org/pkg/biber?lang=en) backend is used.
To include `.bib` files, just use `\addbibresource{your-file.bib}` somewhere in the preamble.

### Preprint Entry Type
The BibLaTeX code defines a non-standard `@preprint` entry.
The citation key inside the document appends a `+` to the year, to indicate non-published status.
An example entry is
```bib
@preprint{example,
  author = {Rutar, Alex},
  eprint = {1111.11111},
  eprinttype = {arxiv},
  title = {An example article},
  year = {2023}
}
```
which will be rendered in the bibliography as

> A. Rutar. *An example article*. Preprint. `arxiv:1111.11111`.

You can also include a `journal` entry (e.g. `journal = {Journal Name}`) in which case it will be rendered as

> A. Rutar. *An example article*. To appear in: Journal Name. `arxiv:1111.11111`.


### Rendering of archive sources
This template (ab)uses the `eprint` and `eprinttype` entries in order to render archive information.
For example, if you include the lines
```bib
eprint = {1337.28015},
eprinttype = {zbl}
```
the corresponding record will be accompanied by a link [`zbl:1337.28015`](https://zbmath.org/1337.28015).

The supported `eprinttype` options are: `arxiv`, `zbl`, `zbmath`, `doi`, `mr`.

### Other BibLaTeX Notes

1. Empty bibliography warnings are suppressed.
2. The `\textcite` command is modified to print the journal name, the pages, and the archive.
3. You can include a journal reference on the first page using `\journal` command in the preamble, which takes exactly one argument.
   If you have the journal reference in your `.bib` file, you can use the `\journalcite` shortcut command in the preamble, which takes exactly one argument.

## Hyperref and references
The packages [hyperref](https://ctan.org/pkg/hyperref?lang=en), [cleveref](https://ctan.org/pkg/cleveref?lang=en), and [ntheorem](https://ctan.org/pkg/ntheorem?lang=en) are loaded with proper ordering and dependencies.
It is recommended to use the `\cref` command to make proper citations.

1. The defined standard environments are: `theorem`, `lemma`, `corollary`, `conjecture`, `proposition`, `question`, `definition`, `notation`, `example`, `remark`, `proof`, `solution`.
2. The defined introduction theorem environments are `itheorem` and `icorollary` which are rendered with letters instead of numbers.
3. There are a few special environments: `nmproof` defines a proof environment without a mark, and the `proofpart` environment is designed to be used inside a `proof` environment to render separate Parts
4. `\hypersetup` is used to generate PDF metadata, which is generated from the authors and the title.
   If your title has math characters in it, you need to use `\texorpdfstring{<tex>}{<string>}` to avoid hyperref errors.

## Display breaks
This template uses `\allowdisplaybreaks`.
In order to prevent unwanted display breaks on certain newlines, use `\\*`.
