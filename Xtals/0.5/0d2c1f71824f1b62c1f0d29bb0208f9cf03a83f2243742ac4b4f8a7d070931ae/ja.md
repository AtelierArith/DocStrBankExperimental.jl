```
r = distance(coords, box, i, j, apply_pbc)
r = distance(atoms, box, i, j, apply_pbc) # atoms i and j
r = distance(charges, box, i, j, apply_pbc) # charges i and j
r = distance(atoms, i, j) # no PBCs, coords must be in Cartesian coords
r = distance(coords, i, j) # no PBCs, coords must be in Cartesian coords
```

粒子 `i` と `j` の間の（直交）距離を計算します。

`apply_pbc` が `true` の場合にのみ周期境界条件を適用します。

# 引数

  * `coords::Coords`: 座標（`Frac>:Coords` または `Cart>:Coords`）
  * `atoms::Atoms`: 原子
  * `charges::charges`: 原子
  * `box::Box`: 単位セル情報
  * `i::Int`: 最初の粒子のインデックス
  * `j::Int`: 2 番目の粒子のインデックス
  * `apply_pbc::Bool`: 周期境界条件を適用したい場合は `true`、そうでない場合は `false`
