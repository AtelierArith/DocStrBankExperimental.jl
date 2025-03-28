```
foldl(op, itr; [init])
```

Comme [`reduce`](@ref), mais avec une associativité gauche garantie. Si fourni, l'argument clé `init` sera utilisé exactement une fois. En général, il sera nécessaire de fournir `init` pour travailler avec des collections vides.

Voir aussi [`mapfoldl`](@ref), [`foldr`](@ref), [`accumulate`](@ref).

# Exemples

```jldoctest
julia> foldl(=>, 1:4)
((1 => 2) => 3) => 4

julia> foldl(=>, 1:4; init=0)
(((0 => 1) => 2) => 3) => 4

julia> accumulate(=>, (1,2,3,4))
(1, 1 => 2, (1 => 2) => 3, ((1 => 2) => 3) => 4)
```
