---
title: "Getting started"
draft: true
hideLastModified: true
showInMenu: false
summaryImage: "images/icon.png"
developer: Andrew Abi-Mansour
summary: "Creating your 1st component"
---

# Getting started
There are infinite ways you could build your own component in MMIC. An easy and quick way to get started is by using
the CMS cookiecutter, which you can install via pip and then interactively run to create a git repository:
{{< code language="bash" line-numbers="false">}}
pip install cokiecutter
cookiecutter gh:molssi/cookiecutter-mmic
{{< /code >}}

After you're done answering all the questions, you should end up with a git directory that has a tree structure similar to this:

{{< code language="bash" line-numbers="false">}}
├── devtools
│   ├── conda-envs
│   ├── legacy-miniconda-setup
│   └── scripts
├── docs
│   ├── _static
│   └── _templates
└── pkg_name
    ├── components
    ├── data
    ├── models
    └── tests
{{< /code >}}
