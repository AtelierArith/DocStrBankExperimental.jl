```
in!(x, s::AbstractSet) -> Bool
```

Si `x` est dans `s`, retourne `true`. Sinon, ajoute `x` à `s` et retourne `false`. Cela équivaut à `in(x, s) ? true : (push!(s, x); false)`, mais peut avoir une implémentation plus efficace.

Voir aussi : [`in`](@ref), [`push!`](@ref), [`Set`](@ref)

!!! compat "Julia 1.11"
    Cette fonction nécessite au moins 1.11.


# Exemples

```jldoctest; filter = r"^  [1234]$"
julia> s = Set{Any}([1, 2, 3]); in!(4, s)
false

julia> length(s)
4

julia> in!(0x04, s)
true

julia> s
Set{Any} with 4 elements:
  4
  2
  3
  1
```
