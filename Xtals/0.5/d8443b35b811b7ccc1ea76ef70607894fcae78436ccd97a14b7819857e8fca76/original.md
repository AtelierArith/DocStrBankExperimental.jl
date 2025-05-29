```
inside_box = inside(frac_coords) # true or false
inside_box = inside(cart_coords, box)
inside_box = inside(molecule, box) # in Cartesian
inside_box = inside(molecule) # in fractional
inside_box = inside(crystal) # in fractional
```

returns true if coords are all inside a box and false otherwise.

if a molecule or crystal is passed, both atoms and charges must be inside the box.

# Arguments

  * `coords::Coords` the coordinates (works for `Cart` and `Frac`)
  * `molecule::Molecule{T}`: a molecule in either `T::Frac` or `T::Cart` coords
  * `crystal::Crystal`: a crystal
  * `box::Box` the box (only needed if Cartesian)
