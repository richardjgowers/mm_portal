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

# Usage
{{< tabsCode
    file1="/content/components/associaters/forcefield/input.md" title1="Input" language1="python" icon1="python"
    file2="/content/components/associaters/forcefield/api.md" title2="API" language2="python" icon2="python"
    file3="/content/components/associaters/forcefield/output.md" title3="Output" language3="python" icon3="python"
>}}

# Design
This packages provides 4 models derived from MMSchema. The input models are:
- [ParamInput](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/models/input.py#L8)
- [ComputeInput](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/models/input.py#L14)

```python
from mmic_ffpa.models.input import ParamInput, ComputeInput
```

The output models are:
- [ParamOutput](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/models/output.py#L12)
- [ComputeOutput](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/models/output.py#L8)

```python
from mmic_ffpa.models.output import ParamOutput, ComputeOutput
```

This package provides 3 components used for associating the force field parameters to a given MMSchema molecule: 
- [PrepComponent](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/components/prep_component.py#L7): pre-processes the input for compute
- [ComputeComponent](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/components/post_component.py#L5): run the compute
- [PostComponent](https://github.com/MolSSI/mmic_ffpa/blob/master/mmic_ffpa/components/post_component.py#L5): post-processes the output

{{< figure src="images/component.png" width="1120" caption="Schematic diagram of the component and its data (schemas) flow.">}}

# Requirements
- [MMElemental](https://github.com/MolSSI/MMElemental)
- [MMIC](https://github.com/MolSSI/mmic)
- [FF translator](/tags/translators)
- [Mol translator](/tags/translators)

# Supported force fields
- [Amber94](https://pubs.acs.org/doi/abs/10.1021/ja00124a002): Second Generation Amber-based force field for the simulation of proteins, nucleic acids, and organic molecules
- [Amber96](): 
- [Amber99](): 
- [Amber99-ILDN]
- [Amber99SB-ILDN](https://pubmed.ncbi.nlm.nih.gov/20408171): Amber-based force field which improves side-chain torsion potentials for the Amber ff99SB protein force field. 
- [Amber03](https://onlinelibrary.wiley.com/doi/abs/10.1002/jcc.10349): Point‐charge force field for molecular mechanics simulations of proteins
- [AMBERGS]
- [Martini](https://pubs.acs.org/doi/10.1021/jp071097f#:~:text=The%20new%20version%2C%20coined%20the,large%20number%20of%20chemical%20compounds):  Coarse-grained force field for biomolecular simulations & organic molecules.
- [Charmm27]():
- [Gromos96-43a1]
- [Gromos96-43a2]
- [Gromos96-45a3]
- [Gromos96-53a5]
- [Gromos96-53a6]
- [Gromos96-54a7]
- [OPLS-AA](https://pubs.acs.org/doi/abs/10.1021/jp003919d): OPLS-based force field for proteins

# Supported engines
- [GMX pdb2gmx](https://manual.gromacs.org/documentation/5.1/onlinehelp/gmx-pdb2gmx.html): part of the [Gromacs](https://www.gromacs.org) software suite
- [Auto Martini](https://github.com/tbereau/auto_martini): automated [MARTINI](http://www.cgmartini.nl) forcefield mapping and parametrization of small organic molecules.
