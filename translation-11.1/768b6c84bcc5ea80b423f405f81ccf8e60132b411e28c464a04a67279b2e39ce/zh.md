```
transpose(F::Factorization)
```

因式分解 `F` 的惰性转置。默认情况下，返回一个 [`TransposeFactorization`](@ref)，但对于具有实数 `eltype` 的 `Factorization`，则返回一个 [`AdjointFactorization`](@ref)。
