```
transpose(F::Factorization)
```

Transposition paresseuse de la factorisation `F`. Par défaut, renvoie une [`TransposeFactorization`](@ref), sauf pour les `Factorization` avec un `eltype` réel, auquel cas renvoie une [`AdjointFactorization`](@ref).
