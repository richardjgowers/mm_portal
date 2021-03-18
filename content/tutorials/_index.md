---
title: "Tutorials"
draft: true
hideLastModified: true
img_path: images/mmic.png
showInMenu: true
# no need for the "summary" parameter as it is not displayed in any previews
---


# Getting started
There are infinite ways you could build your own component in MMIC. An easy and quick way to get started is by using
the CMS cookiecutter, which you can install via pip and then interactively run to create a git repository:
{{< code language="bash" line-numbers="false">}}
pip install cokiecutter
cookiecutter gh:molssi/cookiecutter-cms
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
    ├── data
    └── tests
{{< /code >}}

We're going to create 2 new directories under 'pkg_name': 'components' and 'models'.
{{< code language="bash" line-numbers="false">}}
mkdir pgk_name/components pkg_name/models
{{< /code >}}

The final structure of your repository should now look like this:
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
