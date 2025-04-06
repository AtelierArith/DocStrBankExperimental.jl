```
isposdef!(A) -> Bool
```

Prueba si una matriz es definida positiva (y Hermitiana) intentando realizar una factorización de Cholesky de `A`, sobrescribiendo `A` en el proceso. Ver también [`isposdef`](@ref).

# Ejemplos

```jldoctest
julia> A = [1. 2.; 2. 50.];

julia> isposdef!(A)
true

julia> A
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  6.78233
```
