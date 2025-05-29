```
overlap_flag, overlap_pairs = overlap(frac_coords, box, apply_pbc; tol=0.1)
```

座標が重なっているかどうかを判断します。ここでは、2つの座標が重なっていると定義されるのは、その（直交）距離が `tol` より小さい場合です。

```
overlap_flag, overlap_pairs = overlap(crystal, apply_pbc)
```

`crystal` 内の原子が重なっているかどうかを判断します。これは、各ペアの共有半径の小さい方と比較してペア間の距離を比較することによって決定されます。

# 引数

  * `coords::Frac`: 分数座標 (`Frac>:Coords`)
  * `box::Box`: 単位格子情報
  * `apply_pbc::Bool`: 周期境界条件を適用したい場合は `true`、そうでない場合は `false`
  * `tol::Float64`: 重なりの許容範囲; 粒子間の距離がこれより小さい場合、重なりが発生します
  * `crystal::Crystal`: 重なりのある原子をチェックするための結晶

# 戻り値

  * `overlap_flag::Bool`: 重なりがある場合は `true`、そうでない場合は `false`
  * `overlap_ids::Array{Tuple{Int, Int}, 1}`: 重なっている座標ペアのID e.g. `[(4, 5), (7, 8)]`
