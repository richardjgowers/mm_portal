---
title: "Forcefield parameter associater"
draft: true
hideLastModified: false
developer: Andrew Abi-Mansour
showInMenu: false
summaryImage: "images/icon.png" 
summary: "Generates parameterized molecules from existing force fields"
tags: ["Assemblers", "ForceFields"]
---

{{< siteBlue "Experimental" "https://github.com/MolSSI/mmic_ffpa" >}}
This component is *usable* with a *stable* **API** and **schemas**. However, it is *buggy*.
{{< /siteBlue >}}

# Design

#### Models
This packages provides 4 models derived from MMSchema. The input models are:
- [ParamInput](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/models/input.py): external input that defines the input molecule and which force field to use
- [ComputeInput](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/models/input.py): internal input used for running compute

The output models are:
- [ParamOutput](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/models/output.py): external output that stores the molecule and force field objects
- [ComputeOutput](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/models/output.py): internal output used for storing compute output

{{< figure src="images/component.png" width="1120" caption="Schematic diagram of the component and its data (schemas) flow.">}}

#### Components
There are 3 components used for assigning the force field parameters to a given MMSchema molecule: 
- [PrepComponent](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/components/prep_component.py#L7): pre-processes and validates input needed for compute
- [ComputeComponent](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/components/post_component.py#L5): assigns the force field parameters by calling a specific engine e.g. gmx
- [PostComponent](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/components/post_component.py#L5): post-processes the output

# Snippet
{{< tabsCode
    file1="/content/components/associaters/forcefield/models.md" title1="Models" language1="python" icon1="python"
    file2="/content/components/associaters/forcefield/components.md" title2="Components" language2="python" icon2="python"
>}}

# Requirements
- [MMElemental](https://github.com/MolSSI/MMElemental)
- [MMIC](https://github.com/MolSSI/mmic)
- [FF translator](/tags/translators)
- [Mol translator](/tags/translators)