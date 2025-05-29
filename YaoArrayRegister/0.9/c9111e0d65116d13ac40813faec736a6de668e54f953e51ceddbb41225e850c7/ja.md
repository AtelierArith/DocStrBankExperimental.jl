```
rand_density_matrix([T=ComplexF64], n::Int; nlevel::Int=2, pure::Bool=false)
```

純粋状態の半分を部分トレースすることによってランダムな密度行列を生成します。

!!! note
    生成された密度行列は丸め誤差のため厳密なエルミートではありません。エルミート性を確認する必要がある場合は、`ishermitian`を使用せず、`isapprox(dm.state, dm.state')`を使用するか、明示的に`Hermitian`としてマークしてください。

