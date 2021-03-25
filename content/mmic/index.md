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

# Component design
To be completed ...

# Component types
There are 2 distinct types of components we distinguish for practical considerations. The 1st type is `GenericComponent` which does not perform any scientific tasks. Instead, this component provides input/output schemas specific to an application area (e.g. energy minimization, molecular dynamics, normal mode analysis, etc.), and discovers and runs `SpecificComponent` that has the same input/output schemas provided by `GenericComponent`. Therefore, `SpecificComponent` is tailored to a particular code in an application area (e.g. OpenMM energy minimization, NAMD molecular dynamics, GROMACS normal mode analysis, etc.). 


<p class="aligncenter">
<img src="/images/classes.png" width="1200">
</p>

The main objective behind this approach is to provide an easy and intuitive way of handling common (but not universal) features available in different MM codes. If *feature1* is requested in a workflow, and this feature is available in *MM code1* but not in *MM code2*, `GenericComponent` runs the execution with a `SpecificComponent` that supprots *MM code1*. `GenericComponent` therefore automates the selection and execution of an available and compatible `SpecificComponent` in runtime, enabling a higher level of abstraction.
