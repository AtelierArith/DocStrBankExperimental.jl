```
something(x...)
```

Retourne la première valeur dans les arguments qui n'est pas égale à [`nothing`](@ref), le cas échéant. Sinon, lance une erreur. Les arguments de type [`Some`](@ref) sont déballés.

Voir aussi [`coalesce`](@ref), [`skipmissing`](@ref), [`@something`](@ref).

# Exemples

```jldoctest
julia> something(nothing, 1)
1

julia> something(Some(1), nothing)
1

julia> something(Some(nothing), 2) === nothing
true

julia> something(missing, nothing)
missing

julia> something(nothing, nothing)
ERROR: ArgumentError: No value arguments present
```
