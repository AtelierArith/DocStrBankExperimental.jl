```
c_coords = Cart(f_coords, box)
atoms_c = Cart(atoms_f, box)
charges_c = Cart(charges_f, box)
```

分数座標 `f_coords::Frac` を直交座標 `c_coords::Cart` に変換します。これは `box::Box` を使用します。これにより `Atoms` と `Charges` にも適用されます。
