```
atoms = remove_duplicates(atoms, box, apply_pbc, r_tol=0.1)
charges = remove_duplicates(charges, box, apply_pbc, r_tol=0.1)
```

remove duplicates from atoms or charges.

loops through all pairs of atoms/charges. if a pair is a duplicate, one is deleted.

two atoms are duplicates if both:

  * same species
  * less than a distance `r_tol` apart two charges are duplicate if both:
  * charge values are within `q_tol`
  * less than a distance `r_tol` apart

# arguments

  * `atoms::Atoms`: the atoms
  * `charges::Charges`: the charges
  * `box::Box`: unit cell information
  * `apply_pbc::Bool`: true iff we apply periodic boundary conditions when computing the distance.
  * `r_tol::Float64`: atoms/charges are overlapping if within `r_tol` distance (PBC applied)
  * `q_tol::Float64`: charges have the same charge value if their charges are within `q_tol` of each other
