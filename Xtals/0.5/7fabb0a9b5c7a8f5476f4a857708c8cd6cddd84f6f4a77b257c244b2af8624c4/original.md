```
atoms, bonds = read_mol("molecule.mol")
```

read a `.mol` file, which contains info about both atoms and bonds. see [here](https://chem.libretexts.org/Courses/University_of_Arkansas_Little_Rock/ChemInformatics_(2017)%3A_Chem_4399%2F%2F5399/2.2%3A_Chemical_Representations_on_Computer%3A_Part_II/2.2.2%3A_Anatomy_of_a_MOL_file) for the anatomy of a `.mol` file.

# Arguments

  * `filename::AbstractString`: the path to and filename of the .mol file (must pass extension)

# Returns

  * `atoms::Atoms{Cart}`: the set of atoms read from the `.mol` file.
  * `bonds::MetaGraph`: the bonding graph of the atoms read from the `.mol` file.
  * `bond_types::Array{Int, 1}`: the array of bond types.
