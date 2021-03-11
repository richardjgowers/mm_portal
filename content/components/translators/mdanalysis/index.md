---
title: "MMSchema/MDAnalysis translator"
date: 2021-02-13
draft: true
developer: Andrew Abi-Mansour
affiliation: MolSSI
link: http://www.molssi.org
hideLastModified: false
showInMenu: false
summaryImage: "images/icon.png"
summary: "Provides translators between MMSchema and MDAnalysis"
tags: ["Translators", "MMSchema"]
---


{{< siteBlue "Experimental" "https://github.com/MolSSI/mmic_mda" >}}
This component is *usable* with a *stable* **API** and **schemas**. However, it is *buggy*.

[//]: # (Badges)
[![GitHub Actions Build Status](https://github.com/MolSSI/mmic_mda/workflows/CI/badge.svg)](https://github.com/MolSSI/mmic_mda/actions?query=workflow%3ACI)
[![codecov](https://codecov.io/gh/MolSSI/mmic_mda/branch/master/graph/badge.svg)](https://codecov.io/gh/MolSSI/mmic_mda/branch/master)
[![Language grade: Python](https://img.shields.io/lgtm/grade/python/g/MolSSI/mmic_mda.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/MolSSI/mmic_mda/context:python)

{{< /siteBlue >}}

# Design
This package provides translators between MMSchema and [MDAnalysis](https://github.com/MDAnalysis/mdanalysis). **mmic_mda** provides 3 types of translators for: molecule, forcefield, and trajectory. The models for each type is respectively: MdaMol, MdaFF, and MdaTraj. The `from_schema` and `to_schema` methods in each model use translation components to convert between MMSchema and MDAnalysis.

{{< figure src="images/summary.png" width="1200" caption="Schematic diagram of the component and its data (schemas) flow.">}}

# Snippet
{{< tabsCode
    file1="/content/components/translators/mdanalysis/models.md" title1="Models" language1="python" icon1="python"
    file2="/content/components/translators/mdanalysis/components.md" title2="Components" language2="python" icon2="python"
>}}

### Copyright
Copyright (c) 2021, MolSSI


#### Acknowledgements
 
Project based on the 
[Computational Molecular Science Python Cookiecutter](https://github.com/molssi/cookiecutter-cms) version 1.5.
