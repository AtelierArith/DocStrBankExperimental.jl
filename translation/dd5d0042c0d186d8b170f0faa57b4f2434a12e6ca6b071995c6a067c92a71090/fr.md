```
Vector{T}(missing, m)
```

Construit un [`Vector{T}`](@ref) de longueur `m`, initialisé avec des entrées [`missing`](@ref). Le type d'élément `T` doit être capable de contenir ces valeurs, c'est-à-dire `Missing <: T`.

# Exemples

```jldoctest
julia> Vector{Union{Missing, String}}(missing, 2)
2-element Vector{Union{Missing, String}}:
 missing
 missing
```
