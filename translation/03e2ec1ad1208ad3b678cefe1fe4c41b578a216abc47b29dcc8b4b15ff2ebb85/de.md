```
!==(x, y)
≢(x,y)
```

Gibt immer die entgegengesetzte Antwort wie [`===`](@ref).

# Beispiele

```jldoctest
julia> a = [1, 2]; b = [1, 2];

julia> a ≢ b
true

julia> a ≢ a
false
```
