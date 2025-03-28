```
^(s::Union{AbstractString,AbstractChar}, n::Integer) -> AbstractString
```

Répète une chaîne ou un caractère `n` fois. Cela peut également être écrit comme `repeat(s, n)`.

Voir aussi [`repeat`](@ref).

# Exemples

```jldoctest
julia> "Test "^3
"Test Test Test "
```
