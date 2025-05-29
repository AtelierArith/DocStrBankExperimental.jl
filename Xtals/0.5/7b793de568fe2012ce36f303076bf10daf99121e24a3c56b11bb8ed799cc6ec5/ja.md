```
f_coords = Frac(c_coords, box)
atoms_f = Frac(atoms_c, box)
charges_f = Frac(charges_c, box)
```

直交座標 `c_coords::Cart` を分数座標 `f_coords::Frac` に変換します。`box::Box` を使用します。これは `Atoms` と `Charges` にも適用されます。
