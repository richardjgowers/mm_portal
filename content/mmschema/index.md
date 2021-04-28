---
title: "MMSchema"
date: 2021-02-12
draft: true
hideLastModified: true
showInMenu: true
# no need for the "summary" parameter as it is not displayed in any previews
---

# What is MMSchema?
MMSchema is a specification for classical particle mechanics with emphasis on Molecular Mechanics (MM). The schema provides a standardized language that enables interoperability between
different MM codes without restricting any specific workflow.

{{< figure src="images/mmschema.png" width="664" caption="MMSchema provides a specification that enables interoperability between different MM codes .">}}

Currently, MMSchema is a [JSON](https://www.json.org) schema; comptability with the [hdf5](https://www.hdfgroup.org/solutions/hdf5) format is being developed, and other formats 
such as the Apache [ORC](https://orc.apache.org) are being considered as well.

# Core models
MMSchema adopts an object-oriented view of classical mechanics by dividing it into its constituent core objects: initial state, inter-particle potential, 
and final state (statics) or trajectory (dynamics). Each core model represents a building block that is an integral part of the computation. The 3 core models in MMSchema are:

- Molecule: represents a basic molecule object for MM, or more generally the N-body state in classical mechanics.
- ForceField: represents force fields for MM, or more generally inter-particle potentials in classical mechanics.
- Trajectory: represents trajectories in dynamical systems.

{{< figure src="images/statics.png" width="800">}}

For classical statics, the MMSchema models `Molecule` and `ForceField` would represent the initial/final states and the inter-particle potential, respectively, as shown in the figure above. 
Likewise, `Trajectory` would represent simulation output of dynamical systems as shown below.


{{< figure src="images/dynamics.png" width="800">}}

Each object in MMSchema is uniquely defined by a set of fields and (when suitable) their associated units as well. The schema is designed to be flexible as much as
possible by providing a general specification for computational particle mechanics, but **MMSchema does not standardize any workflow**. Instead, MMSchema strives to provide a starting point 
for specific application areas based on or related to MM such as energy minimization, force field assignment and construction, molecular dynamics, advanced sampling, ... to name a few. 
The schemas for these domains or applications are handled by [MMIC](/mmic) components that define the input and output models for each procedure. Since MMSchema is not restricted to the 
atomic scale, it can also be used for coarse-graining as well as multiscale methods that evolve multiple spatial and/or temporal scales. 
In fact, *any particle-based Newtonian method can use MMSchema and further customize/extend it*.

# How is MMSchema useful in practice?
MMSchema can be used to standardize MM workflows, enable a certain level of interoperability between different MM codes, file formats, etc., and provide basic models for developing [MMIC](/mmic) 
application schemas. The extensibility of MMSchema also makes it suitable as a base schema for coarse-grained and mesoscopic/continuum particle methods such as the discrete element method (DEM), 
material point method (MPM), and smoothed particle hydroynamics (SPH), to name a few. To use MMSchema in python, see [MMElemental](/mmelemental).
