```
coalesce(x...)
```

Renvoie la première valeur dans les arguments qui n'est pas égale à [`missing`](@ref), le cas échéant. Sinon, renvoie `missing`.

Voir aussi [`skipmissing`](@ref), [`something`](@ref), [`@coalesce`](@ref).

# Exemples

```jldoctest
julia> coalesce(missing, 1)
1

julia> coalesce(1, missing)
1

julia> coalesce(nothing, 1)  # renvoie `nothing`

julia> coalesce(missing, missing)
missing
```
