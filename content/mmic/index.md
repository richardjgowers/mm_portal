---
title: "MMIC"
draft: true
hideLastModified: true
img_path: images/mmic.png
showInMenu: true
# no need for the "summary" parameter as it is not displayed in any previews
---


# What is MMIC?
The Molecular Mechanics Interoperable Components (MMIC) project provides a standard for input and output of MM programs by defining the scientific and computational stages of classical MM pipelines, but leaving the implementation up to the developer/user. MMIC attempts to define the “what” of scientific stages without restricting the “how” i.e. MMIC defines only the input and output the implementation must conform to so that end-users can swap out different implementations with minimal effort in their existing pipelines, or workflow tools of their choice.


# What are MM components?
Components in the MMIC world behave like structured "boxes" with a common API. Each component has well-defined input and output schemas, with complete unawareness of other components used in the workflow.

<p class="aligncenter">
<img src="/images/component.png">
</p>

Each component does internal data validation to ensure the input and output models are compliant with the specified schemas. Using any component requires a single class method to be invoked:

{{< code language="python" line-numbers="false">}}
from mmpkg import Component
output = Component.compute(input) 
{{< /code >}}


The MMIC package is written in python. For more info about the API and component design, see the data validation <a href="#data_valid">section</a> and the online <a href="https://github.com/MolSSI/MMIC">documentation</a>.

# Classes of components
There are 2 classes of components we distinguish for practical and design considerations. The 1st class is generic and does not perform any scientific tasks. Instead, it provides input/output schemas 
specific to an application area (e.g. energy minimization, molecular dynamics, normal mode analysis, etc.), and discovers and runs a class II component that has the same input/output schemas. 
A class II component is, in contrast, tailored to a specific code in an application area (e.g. OpenMM energy minimization, NAMD molecular dynamics, GROMACS normal mode analysis, etc.). 

<p class="aligncenter">
<img src="/images/classes.png" width="900">
</p>

A class I component therefore automates the selection and execution of an available and compatible class II component during run time, enabling a higher level of abstraction.
