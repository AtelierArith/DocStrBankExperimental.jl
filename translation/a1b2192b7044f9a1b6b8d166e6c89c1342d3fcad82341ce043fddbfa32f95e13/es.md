```
isposdef(A) -> Bool
```

Prueba si una matriz es definida positiva (y Hermitiana) intentando realizar una factorización de Cholesky de `A`.

Ver también [`isposdef!`](@ref), [`cholesky`](@ref).

# Ejemplos

```jldoctest
julia> A = [1 2; 2 50]
2×2 Matrix{Int64}:
 1   2
 2  50

julia> isposdef(A)
true
```
