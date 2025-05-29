```
r = distance(coords, box, i, j, apply_pbc)
r = distance(atoms, box, i, j, apply_pbc) # atoms i and j
r = distance(charges, box, i, j, apply_pbc) # charges i and j
r = distance(atoms, i, j) # no PBCs, coords must be in Cartesian coords
r = distance(coords, i, j) # no PBCs, coords must be in Cartesian coords
```

calculate the (Cartesian) distance between particles `i` and `j`.

apply periodic boundary conditions if and only if `apply_pbc` is `true`.

# arguments

  * `coords::Coords`: the coordinates (`Frac>:Coords` or `Cart>:Coords`)
  * `atoms::Atoms`: atoms
  * `charges::charges`: atoms
  * `box::Box`: unit cell information
  * `i::Int`: index of the first particle
  * `j::Int`: Index of the second particle
  * `apply_pbc::Bool`: `true` if we wish to apply periodic boundary conditions, `false` otherwise
