% GF(1) gf user manual
% Pavel Petržela <pavel@petrzela.eu>
  Jiří Pavelka <j.pavelka@seznam.cz>
% April 2016

# NAME

gf

# SYNOPSIS

gf [-ih]

# DESCRIPTION

**gf** implements **git flow model**(1) similarly to **git-flow command**(2) with following improvements:

* even simpler usage (with no parameters),
* automatic version number incrementation (file VERSION),
* automatic version history update (file CHANGELOG),
* independent production branches support.

# OPTIONS

-i, --init
:   Initialize current folder to be compatible with git flow model.

-h, --help
:   Show (this) usage.

# INTRODUCTION

**Git flow model** is based on two main branches, _master_ and _dev_:

dev
: * new features or fixes (bugfix)

master
: * main production branch
* also another independent production branches

Temporary branches:

hotfix-#.#.#
: * fixes on production branch
* for automatic creation run ``gf`` on production branch

feature
: * develop new feature
* name of brach should reflect functionality of the feature
* for creation run ``git checkout -b feature_name`` on branch _dev_

release-#.#
: * testing functionality before merge or move to production
* for automatic creation run ``gf``  on branch _dev_

# EXAMPLES

## Init new repository

#. ``cd project_folder``
#. ``gf --init``

## New feature

#. ``git checkout dev``
#. ``git checkout -b feature_name``
#. … some commits …
#. ``gf``

## Hotfix

#. ``git checkout master``
#. ``gf``
#. … fixes followed by commits …
#. ``gf``

## New release

#. ``git checkout dev``
#. ``gf``

## Bugfix on release

#. ``git checkout release-#.#``
#. … fixes followed by commits …
#. ``gf `` (merge only to dev)

## Release to production

#. ``git checkout release-#.#``
#. ``gf``

# REFERENCES

[**git flow model**(1)](http://nvie.com/posts/a-successful-git-branching-model/)

[**git-flow cheatsheet**(2)](http://danielkummer.github.io/git-flow-cheatsheet/)