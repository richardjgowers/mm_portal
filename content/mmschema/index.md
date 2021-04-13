---
title: "MMSchema"
date: 2021-02-12
draft: true
hideLastModified: true
showInMenu: true
# no need for the "summary" parameter as it is not displayed in any previews
---

# What is MMSchema?
MMSchema is a specification for classical mechanics with emphasis on Molecular Mechanics (MM). The schema provides a standardized language that different codes could use to communicate i.e. 
MMSchema attempts to provide a certain level of interoperability for MM without restricting any specific workflows.

{{< figure src="images/mmschema.png" width="664" caption="MMSchema provides a specification that enables interoperability between different MM codes .">}}

# Core models
MMSchema adopts an object-oriented view of classical mechanics by dividing it into its constituent core objects: initial state, inter-particle potential, 
and trajectory. Each core model represents a building block that is an integral part of the computation. The 3 core models in MMSChema are:

- Molecule: represents a basic molecule object for MM, or more generally the initial state in classical mechanics.
- ForceField: represents force fields for MM, or more generally inter-particle potentials for classical mechanics.
- Trajectory: represents trajectories in classical mechanics.

Each object is uniquely defined by a set of fields that (when suitable) have their own units as well. The schema is designed to be as much flexible as 
possible by providing a general specification for computational particle mechanics, but **MMSchema does not standardize any workflow**. Instead, MMSchema strives to provide a starting point 
for specific application areas based on or related to MM such as energy minimization, force field assignment and construction, molecular dynamics, advanced sampling, ... to name a few. 
Since MMSchema is not restricted to the atomic scale, it can also be used for coarse-graining as well as multiscale methods that evolve multiple spatial and/or temporal scales. 
In fact, *any particle-based Newtonian method can use MMSchema and further customize/extend it*.

# How is MMSchema used in practice?
MMSchema can be used to standardize MM workflows, provide interoperability between different MM codes, file formats, etc., and it provides a base schema for developing [MMIC](/mmic) application schemas. 
To use MMSchema in python, see [MMElemental](/mmelemental).
