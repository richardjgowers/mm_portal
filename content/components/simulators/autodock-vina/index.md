---
title: "AutoDock Vina simulator"
date: 2021-02-14
author: MolSSI
draft: true
hideLastModified: false
showInMenu: false
summaryImage: "images/icon.png" 
summary: "Performs molecular docking with AutoDock Vina"
tags: ["Simulators"]
---

{{< siteBlue "Experimental" "https://github.com/MolSSI/mmic_docking" >}}
This component is *usable* with a *stable* **API** and **schemas**. However, it is *buggy*.
{{< /siteBlue >}}

# Usage
{{< tabsCode
    file1="/content/components/simulators/autodock-vina/input.md" title1="Input" language1="python" icon1="python"
    file2="/content/components/simulators/autodock-vina/api.md" title2="API" language2="python" icon2="python"
    file3="/content/components/simulators/autodock-vina/output.md" title3="Output" language3="python" icon3="python"
>}}

# Design
There are 4 models derived from MMSchema. The input models are:
- [DockInput](https://github.com/MolSSI/mmic_docking/blob/master/mmic_docking/models/input.py#L8)
- [ComputeInput](https://github.com/MolSSI/mmic_docking/blob/master/mmic_docking/models/input.py#L14)

```python
from mmic_ffpa.models.input import ParamInput, ComputeInput
```

The output models are:
- [ParamOutput](https://github.com/MolSSI/mmic_docking/blob/master/mmic_docking/models/output.py#L12)
- [ComputeOutput](https://github.com/MolSSI/mmic_docking/blob/master/mmic_docking/models/output.py#L8)

```python
from mmic_ffpa.models.output import ParamOutput, ComputeOutput
```

There are 3 components used in this package for associating the force field parameters to a given MMSchema molecule: 
- [PrepComponent](https://github.com/MolSSI/mmic_docking/blob/master/mmic_docking/components/prep_component.py#L7): pre-processes the input for compute
- [ComputeComponent](https://github.com/MolSSI/mmic_docking/blob/master/mmic_docking/components/post_component.py#L5): run the compute
- [PostComponent](https://github.com/MolSSI/mmic_docking/blob/master/mmic_docking/components/post_component.py#L5): post-processes the output

{{< figure src="images/component.png" width="1120" caption="Schematic diagram of the component and its data (schemas) flow.">}}

# Requirements
- [MMElemental](https://github.com/MolSSI/MMElemental)
- [MMIC](https://github.com/MolSSI/mmic)
- [Mol translator](http://localhost:1313/tags/translators)
- [Autodock Vina]
