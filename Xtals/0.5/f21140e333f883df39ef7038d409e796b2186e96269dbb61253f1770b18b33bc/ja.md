```
atoms = remove_duplicates(atoms, box, apply_pbc, r_tol=0.1)
charges = remove_duplicates(charges, box, apply_pbc, r_tol=0.1)
```

原子または電荷から重複を削除します。

すべての原子/電荷のペアをループします。ペアが重複している場合は、一方が削除されます。

2つの原子が重複しているのは、両方が次の条件を満たす場合です：

  * 同じ種
  * 距離 `r_tol` 未満 2つの電荷が重複しているのは、両方が次の条件を満たす場合です：
  * 電荷値が `q_tol` 内にある
  * 距離 `r_tol` 未満

# 引数

  * `atoms::Atoms`: 原子
  * `charges::Charges`: 電荷
  * `box::Box`: 単位セル情報
  * `apply_pbc::Bool`: 距離を計算する際に周期境界条件を適用する場合は真
  * `r_tol::Float64`: 原子/電荷が重なっているのは `r_tol` 距離内の場合（PBCが適用される）
  * `q_tol::Float64`: 電荷が同じ電荷値を持つのは、電荷が互いに `q_tol` 内にある場合
