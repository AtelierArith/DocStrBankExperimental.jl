```
overlap_flag, overlap_pairs = overlap(frac_coords, box, apply_pbc; tol=0.1)
```

determine if any coordinates overlap. here, two coordinates are defined to overlap if their (Cartesian) distance is less than `tol`.

```
overlap_flag, overlap_pairs = overlap(crystal, apply_pbc)
```

Determine if any of the atoms in `crystal` overlap, as determined by comparing their pairwise distances to the lesser of each pair's covalent radii.

# Arguments

  * `coords::Frac`: the fractional coordinates (`Frac>:Coords`)
  * `box::Box`: unit cell information
  * `apply_pbc::Bool`: `true` if we wish to apply periodic boundary conditions, `false` otherwise
  * `tol::Float64`: tolerance for overlap; if distance between particles less than this, overlap occurs
  * `crystal::Crystal`: a crystal to check for overlapping atoms

# Returns

  * `overlap_flag::Bool`: `true` if overlap, `false` otherwise
  * `overlap_ids::Array{Tuple{Int, Int}, 1}`: ids of coordinate pairs that are overlapping e.g. `[(4, 5), (7, 8)]`
