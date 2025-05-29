```
write_xyz(atoms, filename; comment="")
write_xyz(crystal; comment="", center_at_origin=false)
write_xyz(molecules, box, filename; comment="") # fractional
write_xyz(molecules, box, filename; comment="") # Cartesian
```

write atoms to an .xyz file.

# Arguments

  * `atoms::Atoms`: the set of atoms.
  * `filename::AbstractString`: the filename (absolute path) of the .xyz file. (".xyz" appended automatically if the extension is not provided.)
  * `comment::AbstractString`: comment if you'd like to write to the file.
  * `center_at_origin::Bool`: (for crystal only) if `true`, translate all coords such that the origin is the center of the unit cell.
