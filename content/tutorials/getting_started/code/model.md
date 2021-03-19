from mmelemental.models.base import ProtoModel

__all__ = ["InputModel", "OutputModel"]


class InputModel(ProtoModel):
    """ An input model for mmic_pkg. """

    mol_formula: str


class OutputModel(ProtoModel):
    """ An output model for mmic_pkg. """

    natoms: int
