```bash
  Traceback (most recent call last):
  File "run.py", line 5, in <module>
    input = mmic_pkg.models.InputModel(mol_formula=mfor)
  File "pydantic/main.py", line 400, in pydantic.main.BaseModel.__init__
pydantic.error_wrappers.ValidationError: 1 validation error for InputModel
mol_formula
  str type expected (type=type_error.str)
```
