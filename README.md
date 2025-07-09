git-rewind-time
===============

Bash-based command to rewind time at the latest commit of Git logs

[![Lint](https://github.com/dceoy/git-rewind-time/actions/workflows/lint.yml/badge.svg)](https://github.com/dceoy/git-rewind-time/actions/workflows/lint.yml)

Installation
------------

This command depends on git.

```sh
$ cd /path/to/bin   # a path in ${PATH}
$ curl -SO https://raw.githubusercontent.com/dceoy/git-rewind-time/master/git-rewind-time
$ chmod +x git-rewind-time
```

Example
-------

Rewind the latest commit date for 7 days

```sh
$ git-rewind-time 7 days
```

Usage
-----

```sh
$ git-rewind-time --help
Rewind time at the latest commit of Git logs

Usage:
  git-rewind-time [--debug] [--dry-run] <int> <unit>
  git-rewind-time --version
  git-rewind-time -h|--help

Options:
  --debug           Debug mode
  --dry-run         Execute a dry run
  --version         Print version
  -h, --help        Print usage

Arguments:
  <int>             Amount of time to rewind
  <unit>            Time unit (seconds, minutes, hours, days, weeks, months, years)
```
