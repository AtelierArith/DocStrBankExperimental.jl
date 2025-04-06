```
repeat(s::AbstractString, r::Integer)
```

Répète une chaîne `r` fois. Cela peut être écrit comme `s^r`.

Voir aussi [`^`](@ref :^(::Union{AbstractString, AbstractChar}, ::Integer)).

# Exemples

```jldoctest
julia> repeat("ha", 3)
"hahaha"
```
