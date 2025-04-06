```
issuccess(F::Factorization)
```

Prueba que una factorización de una matriz tuvo éxito.

!!! compat "Julia 1.6"
    `issuccess(::CholeskyPivoted)` requiere Julia 1.6 o posterior.


# Ejemplos

```jldoctest
julia> F = cholesky([1 0; 0 1]);

julia> issuccess(F)
true
```
