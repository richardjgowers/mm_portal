import mmic_pkg

mfor = "CH4"
input = mmic_pkg.models.InputModel(mol_formula=mfor)
output = mmic_pkg.components.Component.compute(input)

print(f"Number of atoms in {mfor} is {output.natoms}")
