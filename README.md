git-rewind-days
===============

Bash-based command to rewind days at the latest commit of Git logs

[![Lint](https://github.com/dceoy/git-rewind-days/actions/workflows/lint.yml/badge.svg)](https://github.com/dceoy/git-rewind-days/actions/workflows/lint.yml)

Installation
------------

This command depends on git.

```sh
$ cd /path/to/bin   # a path in ${PATH}
$ curl -SO https://raw.githubusercontent.com/dceoy/git-rewind-days/master/git-rewind-days
$ chmod +x git-rewind-days
```

Example
-------

Rewind the latest commit date for 7 days

```sh
$ git-rewind-days 7
```

Usage
-----

```sh
$ git-rewind-days --help
Rewind days at the latest commit of Git logs

Usage:
  git-rewind-days [--debug] [--dry-run] <int>
  git-rewind-days --version
  git-rewind-days -h|--help

Options:
  --debug           Debug mode
  --dry-run         Execute a drt run
  --version         Print version
  -h, --help        Print usage

Arguments:
  <int>             Days to rewind
```
