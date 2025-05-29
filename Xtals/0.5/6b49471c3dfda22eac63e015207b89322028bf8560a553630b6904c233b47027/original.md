```
translate_by!(coords, dx)
translate_by!(coords, dx, box)
translate_by!(molecule, dx)
translate_by!(molecule, dx, box)
```

translate `coords` by the vector `dx`. that is, add the vector `dx`.

this works for any combination of `Frac` and `Cart` coords.

modifies coordinates in place.

`box` is needed when mixing `Frac` and `Cart` coords.

note that periodic boundary conditions are *not* subsequently applied here.

if applied to a `molecule::Molecule`, the coords of atoms, charges, and center of mass are all translated.
