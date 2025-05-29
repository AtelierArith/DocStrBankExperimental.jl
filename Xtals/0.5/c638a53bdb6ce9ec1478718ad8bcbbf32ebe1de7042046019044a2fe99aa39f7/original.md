```
c_coords = Cart(f_coords, box)
atoms_c = Cart(atoms_f, box)
charges_c = Cart(charges_f, box)
```

convert fractional coordinates `f_coords::Frac` to Cartesian coordinates `c_coords::Cart`, using the `box::Box`. this works on `Atoms` and `Charges` too.
