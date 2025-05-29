```
rand_density_matrix([T=ComplexF64], n::Int; nlevel::Int=2, pure::Bool=false)
```

Generate a random density matrix by partial tracing half of the pure state.

!!! note
    The generated density matrix is not strict hermitian due to rounding error. If you need to check hermicity, do not use `ishermitian` consider using `isapprox(dm.state, dm.state')` or explicit mark it as `Hermitian`.

