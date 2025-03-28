```
transpose(F::Factorization)
```

Transposición perezosa de la factorización `F`. Por defecto, devuelve una [`TransposeFactorization`](@ref), excepto para `Factorization`s con `eltype` real, en cuyo caso devuelve una [`AdjointFactorization`](@ref).
