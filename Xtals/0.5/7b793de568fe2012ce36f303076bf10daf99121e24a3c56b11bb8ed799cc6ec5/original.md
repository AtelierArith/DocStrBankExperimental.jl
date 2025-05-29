```
f_coords = Frac(c_coords, box)
atoms_f = Frac(atoms_c, box)
charges_f = Frac(charges_c, box)
```

convert Cartesian coordinates `c_coords::Cart` to fractional coordinates `f_coords::Frac`, using the `box::Box`. this works on `Atoms` and `Charges` too.
