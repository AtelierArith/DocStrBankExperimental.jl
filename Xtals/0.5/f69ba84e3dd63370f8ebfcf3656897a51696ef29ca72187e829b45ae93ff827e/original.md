```
write_cif(crystal, filename; fractional_coords=true, number_atoms=true)
write_cif(crystal) # writes to file crystal.name[.cif]
```

Write a `crystal::Crystal` to a .cif file.

# arguments

  * `crystal::Crystal`: crystal to write to file
  * `filename::AbstractString`: the filename of the `.cif` file. if ".cif" is not included as an extension, it will automatically be appended to the `filename` string.
  * `fractional_coords::Bool=true`: write the coordinates of the atoms as fractional coords if `true`. if `false`, write Cartesian coords.
  * `number_atoms::Bool=true`: write the atoms as "C1", "C2", "C3", ..., "N1", "N2", ... etc. to give each atom a unique identifier
