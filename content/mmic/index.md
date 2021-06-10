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
output_model = Component.compute(input_model) 
{{< /code >}}


The MMIC package is written in python. The design and component types in MMIC are discussed in the next 2 sections.

# Component design
All components in MMIC are subclasses of [ProgramHarness]((https://github.com/MolSSI/mmic/blob/main/mmic/components/base/base_component.py#L8)), which is the most fundamental component in MMIC. This class
performs data validation and program execution, and it provides input/output classmethods that return the models associated with the component schemas. Since all components have the same API, using any of 
them implies invoking a single classmethod (`Component.compute`) which internally does the schema validation for the input model, instantiates the component object, calls `Component.execute` method 
that returns the output model, which is finally validated before it is returned to the calling process. This is summarized in the flowchart below for the 
`Component.compute` method.

<p class="aligncenter">
<img src="/images/mmic_flowchart.svg">
</p>

There are several types of subclasses of `ProgramHarness` which are discussed in the next section. For more information on the MMIC design, see the online <a href="https://github.com/MolSSI/MMIC">documentation</a>. 
To learn about how components are designed in practice, see the "getting started" [tutorial](/tutorials/getting_started).

# Component types
There are 3 distinct and general types of *blueprint* components that could be used when designing a new component in MMIC. 
The 1st type is `GenericComponent`, which as the name implies, is meant for general-purpose usage. The input/output schemas in this component are `ProtoModel`.
The 2nd type is `StrategyComponent` which does not perform any scientific tasks. Instead, this component defines input/output classmethods that specify (scientific) schemas specific to an application area 
(e.g. energy minimization, molecular dynamics, normal mode analysis, etc.). The main task of a `StrategyComponent` is to discover and run a compatible `TacticComponent` (3rd type) that must comply with 
input/output schemas provided by `StrategyComponent`. Therefore, `TacticComponent` is tailored to a particular code in an application area (e.g. OpenMM energy minimization, NAMD molecular dynamics, 
GROMACS normal mode analysis, etc.). 

<p class="aligncenter">
<img src="/images/classes.png" width="1200">
</p>

The main objective behind this design is to provide an easy and intuitive way of handling common (but not universal) features available in different MM codes. 
If *feature1* is requested in a workflow, and this feature is available in *MM code1* but not in *MM code2*, `StrategyComponent` runs the execution with a `TacticComponent` that supports *MM code1*. 
`StrategyComponent` therefore automates the runtime selection and execution of an available and compatible `TacticComponent`, enabling a higher level of abstraction.
