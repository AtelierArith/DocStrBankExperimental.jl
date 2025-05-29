```
write_vtk(box, filename; verbose=true, center_at_origin=false)
write_vtk(crystal)
```

Write a `Box` to a .vtk file for visualizing e.g. the unit cell boundary of a crystal. If a `Crystal` is passed, the `Box` of that crystal is written to a file that is the same as the crystal structure filename but with a .vtk extension.

Appends ".vtk" extension to `filename` automatically if not passed.

# Arguments

  * `box::Box`: a Bravais lattice
  * `filename::AbstractString`: filename of the .vtk file output (absolute path)
  * `crystal::Crystal`: a crystal structure object
  * `center_at_origin::Bool`: center box at origin if true. if false, the origin is the corner of the box.
  * `verbose::Bool`: if true, print the name of the written file to the console.
