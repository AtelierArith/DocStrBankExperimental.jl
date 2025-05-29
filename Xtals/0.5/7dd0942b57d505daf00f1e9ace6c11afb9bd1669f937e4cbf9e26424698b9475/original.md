```
write_bond_information(crystal)
write_bond_information(crystal, filename)
write_bond_information(crystal, center_at_origin=false)
write_bond_information(xtal, filename, :cross_boundary => p -> p, "bonds.vtk") # cross-boundary bonds only
write_bond_information(xtal, filename, :distance => d -> d < 1.0, "bonds.vtk") # distance less than 1.0
```

Writes the bond information from a crystal to the selected filename.

# Arguments

  * `crystal::Crystal`: The crystal to have its bonds written to a vtk file
  * `filename::AbstractString`: The filename the bond information will be saved to. If left out, will default to crystal name.
  * `center_at_origin::Bool`: (optional) center the coordinates at the origin of the crystal
  * `bond_filter::Pair{Symbol, Function}`: (optional) a key-value pair of an edge attribute and a predicate function. Bonds with attributes that cause the predicate to return false are excluded from writing.
  * `verbose::Bool`: (optional) if true, prints output file name to console.
