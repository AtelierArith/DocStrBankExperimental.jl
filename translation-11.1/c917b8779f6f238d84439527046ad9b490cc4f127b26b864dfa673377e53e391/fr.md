```
issuccess(F::Factorization)
```

Testez si une factorisation d'une matrice a réussi.

!!! compat "Julia 1.6"
    `issuccess(::CholeskyPivoted)` nécessite Julia 1.6 ou une version ultérieure.


# Exemples

```jldoctest
julia> F = cholesky([1 0; 0 1]);

julia> issuccess(F)
true
```
