```
zero_state([T=ComplexF64], n::Int, subspace; nlevel=2)
```

指定されたサブスペースにゼロ状態の `SubspaceArrayReg` を作成します。

# 引数

  * `T`: オプション、要素タイプ、デフォルトは `ComplexF64` です。
  * `n`: 必須、原子の数（キュービット）。
  * `subspace`: 必須、リッジバーグ状態のサブスペース。
