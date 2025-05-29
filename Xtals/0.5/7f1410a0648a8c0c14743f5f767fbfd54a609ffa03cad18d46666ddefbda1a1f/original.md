```
crystal = Crystal(filename;
    check_neutrality=true, net_charge_tol=1e-4,
    check_overlap=true, convert_to_p1=true,
    read_bonds_from_file=false, wrap_coords=true,
    include_zero_charges=true,
    remove_duplicates=false,
    species_col=["_atom_site_type_symbol", "_atom_site_label"]
    ) # read from file

crystal = Crystal(name, box, atoms, charges) # construct from matter, no bonds, P1-symmetry assumed
```

Read a crystal structure file (.cif or .cssr) and populate a `Crystal` data structure, or construct a `Crystal` data structure directly.

# Arguments

  * `filename::AbstractString`: the name of the crystal structure file (include ".cif" or ".cssr") read from `PATH_TO_CRYSTALS`.
  * `check_neutrality::Bool`: check for charge neutrality
  * `net_charge_tol::Float64`: when checking for charge neutrality, throw an error if the absolute value of the net charge is larger than this value.
  * `check_overlap::Bool`: throw an error if overlapping atoms are detected.
  * `convert_to_p1::Bool`: If the structure is not in P1 it will be converted to P1 symmetry using the symmetry rules from the `_symmetry_equiv_pos_as_xyz` list in the .cif file. (We do not use the space groups name to look up symmetry rules).
  * `read_bonds_from_file::Bool`: Whether or not to read bonding information from cif file. If false, the bonds can be inferred later. note that, if the crystal is not in P1 symmetry, we cannot *both* read bonds and convert to P1 symmetry.
  * `wrap_coords::Bool`: if `true`, enforce that fractional coords of atoms and charges are in [0,1]³ by mod(x, 1)
  * `include_zero_charges::Bool`: if `false`, do not include in `crystal.charges` atoms which have zero charges, in order to speed up the electrostatic calculations. If `true,` include the atoms in `crystal.charges` that have zero charge, ensuring that the number of atoms is equal to the number of charges and that `crystal.charges.coords.xf` and `crystal.atoms.coords.xf` are the same.
  * `remove_duplicates::Bool`: remove duplicate atoms and charges. an atom is duplicate only if it is the same species.
  * `species_col::Array{String}`: which column to use for species identification for `crystal.atoms.species`. we use a priority list: we check for the first entry of `species_col` in the .cif file; if not present, we then use the second entry, and so on.
  * `infer_bonds::Bool`: if true, bonds are inferred automatically. If set, must specify `periodic_boundaries`. By default, bonds are not inferred.
  * `periodic_boundaries::Union{Bool, Missing}`: use with `infer_bonds` to specify treatment of the unit cell boundary.  Set `true` to treat the unit cell edge as a periodic boundary (allow bonds across it); set `false` to restrict bonding to within the local unit cell. By default, no bonds are inferred.
  * `absolute_path::Bool`: set `true` to load from an absolute path instead of the default path stored in `rc[:paths][:crystals]`.

# Returns

  * `crystal::Crystal`: A crystal containing the crystal structure information

# Attributes

  * `name::AbstractString`: name of crystal structure
  * `box::Box`: unit cell (Bravais Lattice)
  * `atoms::Atoms`: list of Atoms in crystal unit cell
  * `charges::Charges`: list of point charges in crystal unit cell
  * `bonds::MetaGraph`: Unweighted, undirected graph showing all of the atoms that are bonded within the crystal
  * `symmetry::SymmetryInfo`: symmetry inforomation
