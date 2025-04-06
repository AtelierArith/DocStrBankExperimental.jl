```
Matrix{T}(rien, m, n)
```

Construire une [`Matrix{T}`](@ref) de taille `m`×`n`, initialisée avec des entrées [`rien`](@ref). Le type d'élément `T` doit être capable de contenir ces valeurs, c'est-à-dire `Nothing <: T`.

# Exemples

```jldoctest
julia> Matrix{Union{Nothing, String}}(rien, 2, 3)
2×3 Matrix{Union{Nothing, String}}:
 rien  rien  rien
 rien  rien  rien
```
