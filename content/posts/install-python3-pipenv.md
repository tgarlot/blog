---
title: "Install Python3 Pipenv"
date: 2020-11-30T05:50:38+01:00
description: "Setup Python3 on macOS"
draft: true
---

References:
* [Using Python on a Macintosh](https://docs.python.org/3/using/mac.html)

By default, macOS is running with Python 2. 

First install Python 3 with Homebrew: `brew install python3`

To run Python's commands in the shell, need to use `python3`as `python`is pointing to the version 2 installation.

Then install `pipenv` with command `pip3 install pipenv`.

{{% note %}}

Don't use Homebrew to install pipenv - [Explanation](https://pipenv.pypa.io/en/latest/install/#installing-pipenv)

Also, for some reasons, even if `pip`is an alias to `pip3`, the installation of pipenv did not work when running `pip install pipenv`. Have to run it with `pip3`...

{{% /note %}}

