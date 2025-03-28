```
clamp(x, T)::T
```

Clampe `x` entre `typemin(T)` et `typemax(T)` et convertit le résultat en type `T`.

Voir aussi [`trunc`](@ref).

# Exemples

```jldoctest
julia> clamp(200, Int8)
127

julia> clamp(-200, Int8)
-128

julia> trunc(Int, 4pi^2)
39
```
