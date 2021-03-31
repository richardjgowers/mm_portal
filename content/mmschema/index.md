---
title: "MMSchema"
date: 2021-02-12
draft: true
hideLastModified: true
showInMenu: true
# no need for the "summary" parameter as it is not displayed in any previews
---

# What is MMSchema?
MMSchema is a specification for the the Molecular Mechanics (MM) world. The schema provides a standardized language that different codes could use to communicate i.e. MMSchema attempts to provide a certain level of interoperability for MM without restricting any specific workflows (see [MMIC](/mmic) for application schemas). 

{{< figure src="images/mmschema.png" width="664" caption="MMSchema provides a specification that enables interoperability between different MM codes .">}}

MMSchema adopts an object-oriented view of the MM world by dividing it into its constituent core objects such as `Molecule`, `ForceField`,  `Trajectory`, etc. Each object is uniquely defined by a set of fields that (when suitable) have their own units as well. The schema is designed to be as much flexible as possible by providing a general specification for computational particle mechanics that serves as a starting point for specific application areas based on or related to MM such as energy minimization, force field assignment and construction, molecular dynamics, advanced sampling, ... to name a few. Since MMSchema is not restricted to the atomic scale, it can also be used for coarse-graining as well as multiscale methods that evolve multiple spatial and/or temporal scales. In fact, *any particle-based method can use MMSchema and further customize/extend it*.

# How is MMSchema used in practice?
Coming soon ...
