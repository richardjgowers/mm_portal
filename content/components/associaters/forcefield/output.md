# Extract MMSchema mol and and its associated ff object
mol, ff = paramOutput.mol, paramOutput.ff

# Validate output
from mmic_param.models.output import ParamOutput
ParamOutput(**paramOutput.dict())