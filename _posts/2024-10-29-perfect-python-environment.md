---
layout: post
title: Perfect Python Environment
date: 2024-10-29 8:25:00
description: making your python thrive
tags: python data-science
categories: programming
thumbnail: assets/img/python-thrive.jpeg
toc:
  sidebar: left
tabs: true
---

## Introduction

The perfect python environment is a subjective term. It depends on what you are working on. If you are working on data science, you might need jupyter lab. If you are working on web development, you might need Django. If you are working on a machine learning project, you might need PyTorch. But there are some tools that are universally useful. In this post, I will show you how to set up the perfect python environment for any project.

We're going to revolve everything around a *python package*, because the code that we're writing should be structured, tested, and documented. Having a python package and living in a virtual environment, will be the best way to make our productivity thrive.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/perfect_python_environment1.png" class="img-fluid" zoomable=true %}
    </div>
</div>
<div class="caption">
    Sunch .venv, much wow.
</div>

## Pre-requisites

Before we get started, you need to have the following installed on your system:

- bash
- curl (`apt install update & apt install curl`)
- git
- unix based system (macOS, Linux, WSL)

If you are on Windows, use WSL. If you are on macOS, you can use the mac specific commands.

<br/>

## TLDR

- UV
- VSCode
- Copilot
- Linting formatting: RUFF
- jupyter lab / ipython (for data science)
- git
- vscode debugger
- dotenv
- pytest
- coverage
- sphinx
- pre-commit

## Step by Step with explanation

<br/>

### 1. UV

Let starts by creating a directory for the work that we're going to do. This could be developing a web app, creating a machine learning model or printing "Hello World" to the console. We're going to call this directory `mypackage`. Pun intended.

```bash
mkdir mypackage
cd mypackage
```

Now `mypackage` is going to be awesome, and of course it's going to be python. If you're working with python, you're going to need a virtual environment, because there a bagilion versions of python available and you want to make sure you're using the right one. There are almost as many virtual environment handlers as there are versions of python. Historically we had pyenv, conda, virtualenv, poetry and more. But now we have a new kid on the block called `uv`. 

`uv` is developed by [astral-sh](https://github.com/astral-sh/uv), it's written in rust and it's blazing fast. The only risk of using `uv` is that the creators will figure out how great it is and they will start to charge us for it. You can install it with the following command:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh

source $HOME/.local/bin/env

uv --version
```

Now that we have `uv` we can create a virtual environment within our package directory. 

```bash
uv venv  # creates a virtual environment in the .venv directory
uv init --name mypackage --lib  # initializes the package
```

This creates a `.venv` directory in our package directory. This is where everything about your python environment will reside. `uv` will also create a `pyproject.toml`, a `README.md`, a `.git` directory, a `.python-version` and a `src` directory.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/perfect_python_environment2.png" class="img-fluid" zoomable=true %}
    </div>
</div>
<div class="caption">
    Starting off with uv
</div>

Let's activate the virtual environment.

```bash
source .venv/bin/activate
```

Now you're in the virtual environment. You can tell by the `(mypackage)` in front of your prompt. Let's install our package.

```bash
uv sync
```

We can check that our package is installed by running the following:

```bash
python
>>> import mypackage
```

### 2. VSCode