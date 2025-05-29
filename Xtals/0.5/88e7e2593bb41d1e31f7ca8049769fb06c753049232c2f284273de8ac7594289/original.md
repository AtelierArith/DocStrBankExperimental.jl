```
sane_bonds = bond_sanity_check(crystal)
```

Run sanity checks on `crystal.bonds`.

  * is the bond graph fully connected? i.e. does every vertex (=atom) in the bond graph have at least one edge?
  * each hydrogen can have only one bond
  * each carbon can have a maximum of four bonds

if sanity checks fail, refer to [`write_bond_information`](@ref) to write a .vtk to visualize the bonds.

Print warnings when sanity checks fail. Return `true` if sanity checks pass, `false` otherwise.
