```
foldr(op, itr; [init])
```

Comme [`reduce`](@ref), mais avec une associativité droite garantie. Si fourni, l'argument clé `init` sera utilisé exactement une fois. En général, il sera nécessaire de fournir `init` pour travailler avec des collections vides.

# Exemples

```jldoctest
julia> foldr(=>, 1:4)
1 => (2 => (3 => 4))

julia> foldr(=>, 1:4; init=0)
1 => (2 => (3 => (4 => 0)))
```
