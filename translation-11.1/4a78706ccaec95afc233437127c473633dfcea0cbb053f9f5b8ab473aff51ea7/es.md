```
UnitLowerTriangular(A::AbstractMatrix)
```

Construye una vista `UnitLowerTriangular` de la matriz `A`. Tal vista tiene el [`oneunit`](@ref) del [`eltype`](@ref) de `A` en su diagonal.

# Ejemplos

```jldoctest
julia> A = [1.0 2.0 3.0; 4.0 5.0 6.0; 7.0 8.0 9.0]
3×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
 7.0  8.0  9.0

julia> UnitLowerTriangular(A)
3×3 UnitLowerTriangular{Float64, Matrix{Float64}}:
 1.0   ⋅    ⋅
 4.0  1.0   ⋅
 7.0  8.0  1.0
```
