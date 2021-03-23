from typing import List, Tuple, Optional
from mmic.components.blueprints import SpecificComponent
from ..models import *

__all__ = ["Component"]


class Component(SpecificComponent):
    """ A sample component that defines the 3 required methods. """

    @classmethod
    def input(cls):
        return InputModel

    @classmethod
    def output(cls):
        return OutputModel

    def execute(
        self,
        inputs: InputModel,
        extra_outfiles: Optional[List[str]] = None,
        extra_commands: Optional[List[str]] = None,
        scratch_name: Optional[str] = None,
        timeout: Optional[int] = None,
    ) -> Tuple[bool, OutputModel]:

        # Convert input dictionary to model
        if isinstance(inputs, dict):
            inputs = self.input()(**inputs)

        natoms = 0
        for symb in inputs.mol_formula:
            if symb.isdigit():
                natoms += int(symb) - 1
            else:
                natoms += 1

        return True, OutputModel(natoms=natoms)
