```
atoms = read_xyz("molecule.xyz")
```

read a list of atomic species and their corresponding coordinates from an .xyz file.

# Arguments

  * `filename::AbstractString`: the path to and filename of the .xyz file

# Returns

  * `atoms::Atoms{Cart}`: the set of atoms read from the .xyz file.
