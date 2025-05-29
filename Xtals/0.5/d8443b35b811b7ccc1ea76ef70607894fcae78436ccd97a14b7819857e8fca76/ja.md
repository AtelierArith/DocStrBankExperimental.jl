```
inside_box = inside(frac_coords) # true または false
inside_box = inside(cart_coords, box)
inside_box = inside(molecule, box) # カルテシアン座標
inside_box = inside(molecule) # 分数座標
inside_box = inside(crystal) # 分数座標
```

すべての座標がボックス内にある場合は true を返し、そうでない場合は false を返します。

分子または結晶が渡される場合、原子と電荷の両方がボックス内に存在する必要があります。

# 引数

  * `coords::Coords` 座標（`Cart` と `Frac` の両方で動作）
  * `molecule::Molecule{T}`: `T::Frac` または `T::Cart` 座標の分子
  * `crystal::Crystal`: 結晶
  * `box::Box` ボックス（カルテシアンの場合のみ必要）
