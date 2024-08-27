# Icebreaker One Technical Docs

Icebreaker One technical documentation. This repository contains the sources for a [mkdocs-material](https://squidfunk.github.io/mkdocs-material/)
build of the technical documentation, including operational guidelines, for the Icebreaker One Trust Framework.

## Viewing the docs

Once released, this documentation will be hosted at https://docs.icebreakerone.org

## Installation

Building the documentation requires [Python 3](https://www.python.org/) or later.

### Install Python dependencies using pipenv

```bash
pip install pipenv
pipenv install
```

## Local editing and testing

### Activate the pipenv shell (only required once)

```bash
pipenv shell
```

### Building a local version of the docs

The documentation uses [mike](https://github.com/jimporter/mike) to manage versioning. This includes a local webserver you can use to test your changes.

```
mike deploy <version> [latest]
```

e.g. if the current edit is to version 1.2 of the documents, which is also the latest (default served on the site):

```
mike deploy 1.2 latest
```

`mike` automatically pushes updates to the `gh-pages` branch locally.

### Serving the site locally

```
mike serve
```

By default, this serves the docs on `http://localhost:8000`, but you can change this with `-a`/`--dev-addr`.

### Edit and test

Unlike `mkdocs`, `mike serve` doesn't automatically refresh when you make changes, so you need to quit `mike serve`,
run `mike deploy` then run `mike serve` again to view changes.

## Pushing completed updates

Each call to `mike deploy` adds a commit to the `gh-pages` branch. This leads to a lot of "junk commits" on the `gh-pages` branch
as you make and test edits. You should reduce these down to a single commit for each substantial change. To do this you will need
to find the commit ID of the last commit before you started editing:

```
git checkout gh-pages
git log
```

This outputs a log of all commits on the branch in reverse order e.g.

```
commit xxxxxxxxxxxxxxxxxxxx4 (HEAD -> gh-pages)
Author: Alice <alice@example.com>
Date:   Fri Dec 16 17:09:21 2022 +0000

    Deployed xxxxxxx to 0.1 with MkDocs 1.4.2 and mike 1.1.2

commit xxxxxxxxxxxxxxxxxxxx3 (HEAD -> gh-pages)
Author: Alice <alice@example.com>
Date:   Fri Dec 16 17:09:21 2022 +0000

    Deployed xxxxxxx to 0.1 with MkDocs 1.4.2 and mike 1.1.2

commit xxxxxxxxxxxxxxxxxxxx2 (HEAD -> gh-pages)
Author: Alice <alice@example.com>
Date:   Fri Dec 16 17:09:21 2022 +0000

    Deployed xxxxxxx to 0.1 with MkDocs 1.4.2 and mike 1.1.2

commit xxxxxxxxxxxxxxxxxxxx1
Author: Alice <alice@example.com>
Date:   Fri Dec 16 14:12:36 2022 +0000

    Update the docs to something interesting

...
```

You need to rebase all your recent local changes on the last meaningful commit - "Update the docs to something interesting" in the above example -
and then re-commit and push that to `gh-pages` on the remote.

```
git reset --soft xxxxxxxxxxxxxxxxxxxx1
git commit -m "My meaningful commit"
git push
```

Finally, assuning you were working in `master`, check out `master` again so you don't accidentally edit the `gh-pages` branch.

```
git checkout master
```

## Updating the glossary

The Python script `build_glossary.py` retrieves the glossary from our gdrive and writes it to `docs/glossary.md`. `mkdocs` doesn't have
any glossary autobuild capabilities so you will need to add links to defined terms manually in the docs. The `Term` field from the
glossary spreadsheet is parsed by the Python script to create an anchor tag on the item in the `glossary.md` file. The ID of the tag is
the term with punctuation renoved and whitespace replaced by "-". For example "Data sensitivity class - shared (A)" has the tag
`Data-sensitivity-class-shared-A` and a link to it would look like
`[Data sensitivity class - shared (A)](glossary.md#Data-sensitivity-class-shared-A)`

### Deactivating the virtual environment

When you've finished editing, you can deactivate the virtual environment, or just close the Terminal window

```
deactivate
```
