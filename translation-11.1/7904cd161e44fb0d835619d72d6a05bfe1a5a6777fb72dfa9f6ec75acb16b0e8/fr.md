```
isassigned(array, i) -> Bool
```

Testez si le tableau donné a une valeur associée à l'index `i`. Retournez `false` si l'index est hors limites ou a une référence indéfinie.

# Exemples

```jldoctest
julia> isassigned(rand(3, 3), 5)
true

julia> isassigned(rand(3, 3), 3 * 3 + 1)
false

julia> mutable struct Foo end

julia> v = similar(rand(3), Foo)
3-element Vector{Foo}:
 #undef
 #undef
 #undef

julia> isassigned(v, 1)
false
```
