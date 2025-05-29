```
write_mol2(xtal, filename="my_xtal.mol2")
```

Write a `Crystal` to disk in the mol2 format.  Includes atoms, bonds, and unit cell.

# Arguments

  * `xtal::Crystal` : the crystal to export
  * `filename::AbstractString` : (Optional) the name of the file to save to.  By default, file is named automatically from `xtal.name`
