# Icebreaker One Technical Docs
Icebreaker One technical documentation. This repository contains the sources for a [mkdocs-material](https://squidfunk.github.io/mkdocs-material/) 
build of the technical documentation, including operational guidelines, for the Icebreaker One Trust Framework.

## Viewing the docs

This documentation is rendered at https://docs.icebreakerone.org

## Installation

Building the documentation requires [Python 3](https://www.python.org/) or later.

Activate virtual environment and install Python dependencies

```
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Local editing and testing


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
````
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
git rebase --soft xxxxxxxxxxxxxxxxxxxx1
git commit -m “My meaningful commit”
git push
```

Finally, assuning you were working in `master`, check out `master` again so you don't accidentally edit the `gh-pages` branch.

```
git checkout master
```
