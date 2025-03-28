```
Matrix{T}(missing, m, n)
```

Construit une [`Matrix{T}`](@ref) de taille `m`×`n`, initialisée avec des entrées [`missing`](@ref). Le type d'élément `T` doit être capable de contenir ces valeurs, c'est-à-dire `Missing <: T`.

# Exemples

```jldoctest
julia> Matrix{Union{Missing, String}}(missing, 2, 3)
2×3 Matrix{Union{Missing, String}}:
 missing  missing  missing
 missing  missing  missing
```
